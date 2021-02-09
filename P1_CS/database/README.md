# Database

- [Database](#Database)
  - Why do we need to use a database?
  - Performance of Database
- [Index](#index)
  - What is Index
  - Data structure of Index
  - Primary index vs Secondary index
  - Composite index
  - What to consider for Index
- [About normalization](#About-normalization)
  - In what context did normalization come about?
  - So what is normalization?
  - What kind of renewal anomalies are there?
  - Advantages and disadvantages of normalization
- [Transaction](#transaction)
  - What is a transaction?
  - Transaction and Lock
  - Transaction characteristics
  - Points to note when using transactions
- [Deadlock](#Deadlock)
  - What is deadlock?
  - Example of deadlock(MySQL)
  - How to reduce the frequency of deadlocks
- [Statement vs PreparedStatement](#statement-vs-preparedstatement)
- [NoSQL](#nosql)
  - Definition
  - CAP theory
    - consistency
    - Availability
    - Network segmentation tolerance
  - Classification by storage method
    - Key-Value Model
    - Document Model
    - Column Model

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Database)

</br>

## Database

### Why do we need to use a database?

Before the database existed, data was managed using a file system. (It is still partially used) Data is stored in each file unit and must be interworked with an independent application to handle these tasks. The problems at this time are data dependency problems, redundancy, and data integrity.

#### Characteristics of the database

1. Data independence
   - Physical independence: Even if the database size is increased or the data file is added or newly added to increase the performance, there is no need to modify the related application program.
   - Logical independence: The database is a logical structure that can satisfy the logical requirements of various applications.
2. Data integrity
   It is a function that prevents the number of cases where incorrect data occurs through multiple paths, and implements data integrity through data validation.
3. Data security
   Security can be implemented for all data by setting account management or access rights so that only authorized users can access the database or resources in the database.
4. Data consistency
   By managing related information in a logical structure, data inconsistency that may occur when only one data is changed can be excluded. In addition, it is possible to exclude the number of cases where only some data is changed during the work and does not match the rest of the data.
5. Minimize data duplication
   The database can solve the problem of data redundancy and data redundancy, which are one of the drawbacks of the file system, by integrating and managing data.

</br>

### Performance of Database?

Database performance issues start with how to reduce disk I/O. Disk I/O refers to reading data after moving the disk header to the location where the data to be read is stored by rotating the platter (original) of the disk drive. At this time, the time it takes to read data is determined in the step of moving the disk header to the read/write position. In other words, it can be seen that the performance of the disk is determined by how much data is recorded at once without moving the position of the disk header.

Therefore, sequential I/O is inevitably faster than random I/O. However, in reality, most of the I/O operations are random I/O. Can't we change random I/O to sequential I/O and execute it? It can be said that the goal of database query tuning starting from this thought is to reduce random I/O itself.

</br>

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Database)

</br>

## Index

### What is Index

An index can literally be said to be the index at the very beginning or end of a book. If you take this analogy as it is and look at the index, the data will be the contents of the book and the address of the record where the data is stored will be the page number in the index list. Even the DBMS takes a long time to retrieve all the data in the database table and get the desired result. So, the index is created as a key/value pair of the column value and the address where the record is stored.

DBMS indexes are always sorted, so it is fast to search for a desired value, but when a new value is added, deleted, or modified, the execution speed of the query statement is slow. In conclusion, in DBMS, index is a function that sacrifices data storage performance and increases data read speed instead. If all the columns used in the WHERE conditional clause of the SELECT query statement are created as indexes, data storage performance decreases and the size of the index becomes large, which can only bring about adverse effects.

</br>

### Data structure of Index

Then, how does DBMS manage indexes?

#### B+-Tree Index algorithm

The commonly used index algorithm is the B+-Tree algorithm. The B+-Tree index is an algorithm that indexes using the original value without changing the column value (in fact, only the front part of the value is truncated and managed).

#### Hash Index algorithm

It is an algorithm that calculates and indexes hash values from column values, and supports very fast search. However, since the value is modified and indexed, a hash index cannot be used when searching only a part of the value, such as forward matching, which searches for a value starting with a specific character. It is mainly used in memory-based databases.

#### Why use b-tree to create index

I think a hash table with time complexity of accessing data is O(1) more efficient? The condition of the SELECT query also includes an inequality (<>) operation. If a hash table is used, a problem occurs in the case of an inequality operation rather than an equal sign (=) operation. The `hashtable` specialized in the equality operation (=) is not suitable as a data structure for a database.

</br>

### Primary Index vs Secondary Index

Cluster is mainly used to mean grouping several, but clustered indexes are not very different. In the index, clustered is implemented in the form of grouping and storing similar things, which is mainly conceived in that similar values ​​are often searched at the same time. Similar values ​​here refer to data stored in physically adjacent places.

The clustered index is applied only to the primary key of the table. In other words, storing records with similar primary key values ​​is expressed as a clustered index. In a clustered index, the storage location of the record is determined by the primary key value, and when the primary key value is changed, the physical storage location of the record must also be changed. That's why you need to carefully determine the primary key and use a clustered index.

Only one clustered index can be created per table. This is because it is applied only to the primary key, whereas multiple non-clustered indexes can be created per table.

</br>

### Composite Index

The property of the field set as an index is important. If the index is set in the order of title and author, the effect of creating the index can be seen when searching for a title. However, when searching only by author, creating an index is useless. Therefore, how to perform the SELECT query has a lot of influence on how to create the index.

</br>

### What to consider for Index

Is INDEX always good, which significantly improves the performance of SELECT queries? It improves the performance of query statements. Wouldn't it be faster if INDEX was created in all columns?
\_It is not so to speak from the conclusion.
First of all, the first reason is that when INDEX is created, a separate process additionally occurs when executing INSERT, DELETE, and UPDATE query statements. In the case of INSERT, data for INDEX must also be added, so performance is lost. In the case of DELETE, the value existing in INDEX is not deleted and remains as an indication that it is not used. That is, the number of rows remains the same. What if this task is repeated?

The actual data is 100,000, but it could result in 1 million data. When this happens, the index will no longer function. In the case of UPDATE, problems in the case of INSERT and DELETE are simultaneously accompanied. This is because old data is deleted and new data comes in there. In other words, the data before the change is not deleted, and split due to insert occurs.

But more importantly, the performance of the index can be adversely affected depending on the type of data that makes up the column. In other words, creating an index according to the type of data is efficient and there is an inefficient data type. In what case?

Consider a table with three fields: `name`, `age`, and `gender`.
It is easy to predict that the name will have a number of all kinds of cases, the age will have an INT type, and the gender will only have data for both male and female cases. In this case, is it efficient to create an index for which column? To start with, it is efficient to create an index only for names.

Why is gender or age inefficient when indexing?
Suppose that you create an index on gender in units of 2000 for a table corresponding to 10000 records. Genders with a small range of values ​​are inefficient as they read the index and once again cause disk I/O.

</br>

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Database)

</br>

## About normalization

### 1. In what context did normalization come about?

Mixing the attributes of multiple entities in one relation results in redundant storage of information and waste of storage space. Also, due to the duplicated information,'update abnormality' occurs. If the same information is changed in one relation and not changed in the other relations, it is impossible to know which one is correct. To solve this problem, it goes through a normalization process.

#### 1-1. What kind of renewal anomalies are there?

- Insertion anomalies
  It refers to a problem that occurs when unwanted data is inserted or cannot be inserted due to insufficient data.

- Deletion anomalies
  I want to delete only one data, but this refers to a problem in which unwanted information loss occurs because the entire tuple containing the data is deleted.

- Modification anomalies
  This refers to a problem in which accurate information cannot be grasped because inaccurate or partial tuples are updated, and information becomes ambiguous or inconsistent.

</br>

### 2. So what is normalization?

This is the work of structuring data to minimize duplication in a relational database. More specifically, it refers to the work of dividing the attributes of an unsatisfied **bad** relation into smaller **good** relations. After going through the normalization process, the normal form is satisfied. The canonical form refers to the form of the schema of the relation that satisfies certain conditions, and the first normal form, the second normal form, the third normal form,… Etc. exist.

#### 2-1. How to grasp the'bad' relation?

Determines functional dependency between attributes that make up an entity. The determined functional dependency is used as a formal criterion for good relation design. That is, the normal form is defined according to which functional dependency is satisfied for each normal form, and the normal form that does not satisfy the normal form is recognized as a bad relation.

#### 2-2. What is a functional dependency?

Functional dependency is a kind of constraint derived from the meaning of attribute data and the interrelationships between attributes. Assuming that X and Y are arbitrary sets of attributes, if the value of X determines the value of Y uniquely, then "X determines Y functionally." Functional dependencies are derived from constraints between attributes that exist in the real world. In addition, functional dependencies between attributes can be determined according to various inference rules.
\_cf> The set of all functional dependencies that can be inferred based on the functional dependencies inferred from the relationship of attributes is called closure.

#### 2-3. What conditions must each normalization satisfy?

1. The decomposition set D, which is the target of decomposition, must guarantee **lossless join**.
2. Decomposition set D must preserve functional dependencies.

</br>

### 1st normal form

The attribute's domain must contain only `atomic values', and all attributes in the tuple must have one value belonging to the domain. In other words, it refers to a type of relation that does not allow non-atomic attributes such as compound attributes, multi-value attributes, and nested relations.

### 2nd normal form

If all non-major attributes are **fully functionally dependent** on the main attribute, it can be considered as satisfying the second normal form. Fully functional dependency is a case where, assuming `X -> Y`, a functional dependency is no longer established when any attribute of X is removed. In other words, it refers to a relation type in which non-key columns are determined for each candidate key.

### 3rd normal form

It can be said that any non-major attribute satisfies the 3rd canonical form if **performatively not dependent** on the primary key. Transitional functional dependency refers to the dependency of `X -> Z` that can be inferred by the case of `X ->Y` and `Y -> Z`. In other words, it refers to a form of relation in which non-major attributes are not subordinated by non-major attributes.

### BCNF(Boyce-Codd) normal form

This is the normalization content corresponding to a relation in which several candidate keys exist. It is meaningful to supplement the third canonical form in order to solve the problem caused by the complex identifier relationship. This is the decomposition process in which non-major attributes determine part of the candidate key.

Each canonical form has more stringent conditions than its preceding canonical form.

-Every second normal form relation has a first normal form.
-All third normal form relations have a second normal form.
-All BCNF canonical relations have a third canonical form.

There are many canonical forms, but the goal of relational database design is to ensure that each relation has 3NF (or BCNF).

</br>

### 3. What are the advantages of normalization?

1. Remove anomaly when changing database
   It is possible to solve the problem that various abnormal phenomena mentioned above occur.

2. Minimize redesign when expanding database structure
   In the normalized database structure, when expansion due to the addition of a new data type, the structure may not be changed or only a part may be changed. This has minimal impact on the application program linked with the database and extends the life of the application program.

3. Give users more meaningful data models
   The relations between normalized tables and normalized tables reflect concepts in the real world and their relationships.

</br>

### 4. Are there any disadvantages?

Due to the decomposition of the relation, there are many operations (JOIN operations) between relations. This can slow down the response time to a query.
To add a bit, performing normalization removes more than just input/modify/delete with a general property that has a functional dependency by the determinant that determines the data. Since the redundant attributes of data are removed and general attributes of the same meaning are aggregated into one table by the decision maker, the data capacity of one table is minimized. Therefore, normalized tables have characteristics that can be faster or slower when processing data.

</br>

### 5. From the downside, in what situations should normalization be performed? What is the countermeasure for the shortcomings?

In the case where many joins occur in the SQL statement to be played and the resulting performance decreases, a strategy to apply anti-normalization is needed.

#### De-normalization

'Semi-normalization' is one of the data modeling techniques that perform redundant integration and separation of normalized entities, attributes, and relationships to improve system performance and simplify development and operation. If the performance is degraded when searching due to a large amount of disk I/O, performance degradation due to joins is expected because the path between tables is too far, or when performance is expected to decrease when searching by calculating columns, semi-normalization is performed. . In general, semi-normalization is considered partially when it is judged that the processing performance for inquiries is important.

#### 5-1. What is the object of anti-normalization?

1. When the number of processes that access frequently used tables is the largest and always searches only a certain range
2. When there is a large amount of data in the table, when processing a large range frequently, there is a performance issue
3. When it is technically difficult to retrieve data due to excessive use of joins on the table

#### 5-2. What should be noted in the semi-normalization process?

Excessive application of anti-normalization can break data integrity. In addition, the response time for input, modification, or deletion queries may be delayed.

</br>

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Database)

</br>

## Transaction

### What is a transaction?

Transactions guarantee the **completeness** of the work. In other words, it is a function that completely processes all logical set of tasks, or restores them to their original state when they cannot be processed, so that only part of the tasks is not applied. From the user's point of view, it can be understood as a logical unit of work, and from the point of view of the system, it is a unit of a program that accesses or changes data.

</br>

### Transaction and Lock

Lock and transaction are similar concepts, but in fact, lock is a function to control concurrency, and transaction is a function to ensure data consistency. Locking plays a role in allowing only one connection to be changed at a time in order when multiple connections request the same resource at the same time. Here, resources are records or tables. On the contrary, a transaction is not necessarily a meaningful concept only when queries that perform several changes are combined. A transaction guarantees that the logical work set itself is 100% applied or nothing is applied, regardless of whether there is one query in one logical work set or two or more queries. For example, when there is a failure in work due to a problem such as HW error or SW error, special countermeasures are required to solve this problem.

</br>

### Transaction characteristics

_What characteristics should a transaction satisfy?_
Transaction must satisfy the following four characteristics of ACID.

#### Atomicity

If any problem occurs in the middle of a transaction, no work content corresponding to the transaction must be performed, and all work must be performed only when no problem occurs.

#### Consistency

Even in the state after the transaction is completed, data consistency must be guaranteed in the same way as before the transaction occurred.

#### Isolation

Each transaction must be performed independently without interfering with each other.

#### Durability

After the transaction is normally terminated, the result of the operation must be permanently stored in the database.

</br>

### transaction status

<!-- ![transaction status diagram](/Database/images/transaction-status.png) -->

#### Active

The activity state of the transaction. It is a state in which a transaction is running and is running.

#### Failed

Transaction failure status. It is a state in which the transaction can no longer proceed normally.

#### Partially Committed

The transaction `Commit` command has arrived. Refers to the status of executing the `sql` statement before `commit` of the transaction and only `commit` remains.

#### Committed

Transaction completion status. It is the state in which the transaction has been normally completed.

#### Aborted

The transaction is canceled. This is the state in which the transaction was canceled and the data before the transaction was executed.

#### Difference between Partially Committed and Committed

When a `Commit` request comes in, the status becomes `Partial Commited`. After that, if `Commit` can be executed without any problem, it is transferred to the `Committed` state, and if an error occurs, it becomes the `Failed` state. In other words, `Partial Commited` means when a `Commit` request is received, and `Commited` means the status of successfully completing `Commit`.

### Points to note when using transactions

It is recommended to apply transactions only to the minimum necessary code. In other words, it means to minimize the scope of the transaction. In general, the number of database connections is limited. However, if the time for each unit program to own a connection increases, the number of available free connections decreases. Then, at some point, you may have to wait for each unit program to get a connection.

### Deadlock

#### What is a deadlock

Deadlocks can occur when using multiple transactions. Deadlock is a state in which two or more transactions acquire a lock on a specific resource (table or row) and request a lock owned by another transaction, and the situation does not change no matter how long they wait. This is called a'deadlock'. do.

#### Deadlock Example (MySQL)

Because of the characteristics of MySQL [MVCC](https://en.wikipedia.org/wiki/Multiversion_concurrency_control), a lock is acquired when an update operation (Insert, Update, Delete) is executed in a transaction. (Default lock on row)

![classic deadlock source: https://darkiri.wordpress.com/tag/sql-server/](/Database/images/deadlock.png)

Suppose transaction 1 acquires a lock on the first row of table B and transaction 2 also acquires a lock on the first row of table A.

```SQL
Transaction 1> create table B (i1 int not null primary key) engine = innodb;
Transaction 2> create table A (i1 int not null primary key) engine = innodb;

Transaction 1> start transaction; insert into B values(1);
Transaction 2> start transaction; insert into A values(1);
```

If you request a lock on each other's first row without committing the transaction

```SQL
Transaction 1> insert into A values(1);
Transaction 2> insert into B values(1);
ERROR 1213 (40001): Deadlock found when trying to get lock; try restarting transaction
```

Deadlock occurs. A general DBMS independently detects and reports deadlocks.

#### How to reduce the frequency of deadlocks

-Commit transactions frequently.
-Access the table in a fixed order. Transaction 1 above accessed table B -> A in the order,
Transaction 2 was accessed in the order of table A -> B. Make transactions access in the same table order.
-Avoid using read lock acquisition (SELECT ~ FOR UPDATE).
-Deadlocks are likely to occur if multiple rows of a table are updated without order in multiple connections. In this case, concurrency decreases by serializing the update by acquiring a table-level lock, but the deadlock can be avoided.
</br>

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Database)

</br>

## Statement vs PreparedStatement

First of all, it is known that `PreparedStatement` is fast in terms of speed. The reason is that the query has already been compiled before the query is executed, and in the case of repeated execution, the execution is performed through the precompiled query.

In `PreparedStatement`, `static sql`, which sets and binds variables, is usually used, and in `Statement`, `dynamic sql`, which puts a condition into the query itself, is used. It is clear that `PreparedStatement` reduces the parsing time, but we cannot help but consider the performance degradation associated with using `static sql`.

However, when considering performance, it is the process of fetching rows from the table that takes up the largest portion of the time, and the time to parse the SQL statement is only one tenth of this time. Therefore, it is correct to use `PreparedStatement` that complements problems such as `SQL Injection`.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Database)

</br>

## NoSQL

### Definition

It **avoids** the relational data model and is specialized for storing and retrieving large amounts of distributed data. It is a repository that can be used without a schema or that provides a loose schema.

Each type has unique features such as specialized write/read performance, secondary index support, and auto sharding support. In order to process a large amount of data quickly, temporary storage in memory and a response are used. It also supports dynamic scale-out, and provides performance and features that relational databases cannot provide by means of data replication for availability.

</br>

### CAP theory

### 1. Consistency

Consistency is also referred to as concurrency or identity, and it means ensuring that data retrieved from multiple clients at the same time is always the same data. This is the most basic function supported by a relational database, but if you use NoSQL that does not support consistency, the consistency of the data is loosely handled and the same data may not appear. Loosely handled means propagating data changes to multiple nodes over time. This method is said to support final consistency or ultimate consistency by saying that the final consistency is maintained.

Each NoSQL uses two methods for data synchronization between distributed nodes.
First, there is a synchronous method of storing data in all nodes before responding to the data storage result to the client. It shows a slow response time, but guarantees data consistency.
Second, there is an asynchronous method of writing to memory or a temporary file, responding to the client first, and then synchronizing the data to the node using specific events or processes. Although it has the advantage of showing a fast response time, data may be lost if a failure occurs in the write node.

</br>

### 2. Availability

Availability guarantees that all client read and write requests must always be responded to, and is also referred to as fault tolerance. NoSQL with fault tolerance can provide normal service even if several nodes in the cluster fail.

Some NoSQL uses data replication to ensure availability. This is a method of storing the same data redundantly in multiple nodes so that data is not lost even if several nodes fail. There are two methods of data redundant storage: Master-Slave replication, which creates another storage with the same data, and Peer-to-Peer, which redundantly stores data in units of data.

</br>

### 3. Network Partition Tolerance

Division allowance means that in a system operating in a regionally divided network environment, even if the network between two regions is disconnected or network data is lost, the system within each region must operate normally.

</br>

### NoSQL classification according to storage method

It can be classified into `Key-Value Model`, `Document Model`, `Column Model`, and `Graph Model`.

### 1.Key-Value Model

It is the most basic form of NoSQL and has a single key-value structure that can store and retrieve one data with a single key. It does not support complex search operations due to its simple storage structure. In addition, it is often optimized for high-speed reading and writing. It is used for storing user profile information, session information for web server clusters, shopping cart information, and URL shortening information. If multiple data inquiry and modification operations occur in one service request, transaction processing is impossible and data consistency cannot be guaranteed.
_ex) Redis_

### 2. Document Model

It is a conceptually extended structure of the key-value model, which stores and retrieves one structured document in one key. The logical data storage and retrieval method is similar to the relational database. The key is expressed as an ID for the document. Also, it manages the stored documents as a collection and creates an index for the document ID at the same time as the document is saved. You can retrieve the document within O(1) hours by using the index for the document ID.

Most document models NoSQL use B-tree indexes to create secondary indexes. As the size of the B tree increases, the performance decreases when new data is input or deleted. Therefore, the best performance is achieved when the ratio of read to write is around 7:3. It is used for centralized log storage, timeline storage, and statistical information storage.
_ex) MongoDB_

### 3. Column Model

Stores and retrieves data consisting of pairs of several column names and column values ​​in one key. All columns are always stored with time stamp values.

Google's big table is a typical example, and the subsequent column-type NoSQL was influenced by big tables. For this reason, big table concepts such as row key, column key, and column family are commonly used. The basic unit of storage is a column, and a column consists of a column name, column value, and timestamp. The set of these columns is a row, and a row key is a value that uniquely identifies each row. The set of these rows becomes a key space.

Most column models, NoSQL, are more specialized for writing while reading and writing. It provides fast response speed because data is first saved in the commit log and memory and then responds. Therefore, it shows the best performance when implementing a service that requires many write operations versus read operations or a service that inputs and searches a large amount of data in a short time. It is suitable for implementing services such as saving chat contents and data storage for real-time analysis.

[Back](https://github.com/jojo-tey/Today_I_Learned)/[Top](#Database)

</br>

</br>

_Database.end_
