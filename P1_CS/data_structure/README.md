# Data Structure

- [Interview Question for Data structures](#Interview-Question-for-Data-structures)
- [Array vs Linked List](#Array-vs-Linked-List)
- [Stack and Queue](#Stack-and-Queue)
- [Tree](#Tree)
  - Binary Tree
  - Perfect Binary Tree
  - Complete Binary Tree
  - Full Binary Tree
  - BST(Binary Search Tree)
- [Binary Heap](#Binary-Heap)
- [Red Black Tree](#Red-Black-Tree)
  - Definition of Red-Black Tree
  - Characteristics of Red-Black Tree
  - Insertion
  - Delete
- [Hash Table](#hash-table)
  - Hash Function
  - Resolve Collision
    - Open Addressing
    - Separate Chaining
  - Resize
- [Graph](#graph)
  - Graph terms
  - Graph implement
  - Graph search
  - Minimum Spanning Tree
    - Kruskal algorithm
    - Prim algorithm



[Back](https://github.com/jojo-tey/Today_I_Learned)/[Top](#Data-Structure)




## Interview Question for Data structures

* [Top 15 Data Structures and Algorithm Interview Questions for Java programmer](http://javarevisited.blogspot.com.by/2013/03/top-15-data-structures-algorithm-interview-questions-answers-java-programming.html)
* [Top 50 Data Structure Interview Questions from Career Guru](http://career.guru99.com/top-50-data-structure-interview-questions/)
* [What is Data Structure? | Top 40 Data Structure Interview Questions](https://www.interviewbit.com/data-structure-interview-questions/)



[Back](https://github.com/jojo-tey/Today_I_Learned)/[Top](#Data-Structure)



</br>

## Array vs Linked List

</br>

### Array

</br>

The most basic data structure, the Array data structure, has the same logical and physical storage order. Therefore, you can access the element by index. Therefore, if you know the index value of the element you are looking for, you can access Big-O(1) as the element. In other words, it has the advantage that random access is possible.

However, in the process of deleting or inserting, it takes more time because you have to access the element and complete the task (O(1)), and then perform another task additionally. If an element of an array is deleted, the successive characteristics of the array are broken. In other words, there is an empty space. Therefore, the cost of shifting elements having an index larger than the deleted element is incurred, and the time complexity in this case becomes O(n). Therefore, the worst case of the time complexity for the delete function in the Array data structure is O(n).

The same is true for insertion. If you want to add a new element to the first digit, you need to shift the indexes of all elements by 1, so in this case, it also requires O(n) time.

</br>

### Linked List

</br>

The data structure for solving this problem is a linked list. Each element only remembers what element it is after itself. Therefore, if only this part is changed to a different value, deletion and insertion can be solved in O(1).

However, linked lists also have one problem. If you want to insert at a desired position, you have to check all the first elements in the search process for the desired position. This is because the logical storage order and physical storage order do not match, unlike Array. This is like inserting and sorting once. Because of this process, when an element is deleted or added, O(n) time is additionally generated to find the element.

After all, the linked list data structure has O(n) time complexity for search and O(n) time complexity for insertion and deletion. This is not a very useless data structure, so we are learning. This Linked List is a data structure that is the basis of the Tree structure, and its usefulness is revealed when used in Tree.

</br>

[Back](https://github.com/jojo-tey/Today_I_Learned)/[Top](#Data-Structure)

## Stack and Queue

</br>

### Stack

</br>

Last In First Out (LIFO) as a type of linear data structure. In other words, the element entered later comes out first. This is the biggest feature of the Stack. It is a structure that stacks up one by one, and the elements that first enter the stack are laid on the bottom. Therefore, the ones who entered late are piled up on top of them, and the top one is called when calling.

### Queue

</br>

First In First Out (FIFO) as a type of linear data structure. That is, the one who entered first comes out first. Contrary to the stack, the person who entered first waits at the front, and then comes out first. For reference, in Java Collection, Queue is an interface. Priority queues that implement this can be used.

</br>

[Back](https://github.com/jojo-tey/Today_I_Learned)/[Top](#Data-Structure)

## Tree

</br>

### Binary Tree

</br>

It is divided into two sub-trees (a small tree belonging to a large tree) around the root node. Also, both divided subtrees must be binary trees. It seems that it is a recursive definition, but it does not seem to be easy to understand. As an addition, we need to include the empty set as a binary tree. This is because the definition is satisfied when the condition is checked recursively and when it is attached to the leaf node. Naturally, even having only one node is satisfied with the binary tree definition.

In the tree, each layer is numbered and called the level of the tree. The level value starts from 0, so the level of the root node is 0. And, referring to the highest level of the tree, it is called the height of the tree.

</br>

### Perfect Binary Tree, Complete Binary Tree, Full Binary Tree

</br>

A binary tree full of all levels is called a saturated binary tree. A binary tree that is filled in order from top to bottom and left to right is called a complete binary tree. A binary tree in which all nodes have only 0 or 2 child nodes is called a positive binary tree. In a binary tree consisting of an array, when the number of nodes is n and the root starts at 1 instead of 0, parent(i) = i/2, left_child(i) = 2i, right_child(i) = 2i + for the i-th node. It has an index value of 1.

### BST(Binary Search Tree)

For an efficient search, you shouldn't just worry about how to find it. Rather, we have to think about what is the storage method for efficient search. The binary search tree is a kind of binary tree. However, there are rules for storing data in the binary search tree. And that rule can be used to locate specific data.

- Rule 1. The keys stored in nodes of the binary search tree are unique.
- Rule 2. The height of the parent is greater than the height of the left child node.
- Rule 3. The parent's key is less than the right child node's key.
- Rule 4. The left and right subtrees are also binary search trees.

The search operation of a binary search tree has a time complexity of O(log n). In fact, to be precise, it is correct to express it as O(h). This is because the number of nodes that can be added doubles as the height of the tree increases one by one. However, such a binary search tree can be a Skewed Tree. This is because nodes are continuously added to only one side according to the storage order. In this case, it affects the performance, becomes the Worst Case of the search, and the time complexity becomes O(n).

Although it uses more memory than an array and stores data, there is an inefficient situation where the time complexity required for search becomes the same. To solve this problem, a rebalancing technique appeared. The rebalancing of the tree structure for balancing is called rebalancing. There are several types of trees that implement this technique, and one of them is the Red-Black Tree

</br>

[Back](https://github.com/jojo-tey/Today_I_Learned)/[Top](#Data-Structure)

## Binary Heap

</br>

As a kind of data structure, it is in the form of a tree, and among the trees, it is a Complete Binary Tree based on an array. When putting the values ​​of the tree into the array, the 0th is skipped and the root node starts from the 1st index. This is to reduce confusion by matching the unique number value of the node and the index of the array. There are two types of heap: max heap and min heap.

Max Heap refers to a complete binary tree where the value of each node is greater than or equal to the value of the children. (Min Heap is the opposite.)

In Max Heap, the value in the root node is the largest, so the time complexity of the operation required to find the maximum value is O(1). And because it is a complete binary tree, it can be managed efficiently using an array. (In other words, random access is possible. In Min heap, the time complexity of the operation required to find the minimum value is O(1).) However, in order to keep the structure of the heap, another node to replace the removed root node is required. . Here, the heap replaces the last node with the root node and then goes through heapify again to maintain the heap structure. In this case, the maximum or minimum value can be approached with a time complexity of O(log n).

</br>

[Back](https://github.com/jojo-tey/Today_I_Learned)/[Top](#Data-Structure)

## Red Black Tree

RBT (Red-Black Tree) is a tree-type data structure based on BST. To start with the conclusion, when data is saved in the Red-Black Tree, O(log n) time complexity is required for Search, Insert, and Delete. When the number of nodes is the same, the key idea is to minimize the depth to reduce the time complexity. When the number of nodes is the same, the minimum depth is when the tree is a complete binary tree.

</br>

### Definition of Red-Black Tree

Red-Black Tree is a BST that satisfies the following properties.

1. Each node has a color of red or black.
2. The color of the root node is Black.
3. Each leaf node is black.
4. If a node's color is red, the color of both children is black.
5. For each node, the simple path from node to descendant leaves all contains the same number of black nodes. This is called the Black-Height of the corresponding node.
   > Black-Height: The number of black nodes on a simple path from node x to leaf node not including node x

### Characteristics of Red-Black Tree

As it is a binary search tree, it has all the features of BST.
Among all the paths from the root node to the leaf node, the size ratio of the minimum and maximum paths is not greater than 2. This state is called the balanced state.
If there is no child of the node, the pointer to child stores the NIL value. These NILs are regarded as leaf nodes.
RBT is a data structure created to solve problems that may occur in the process of inserting and deleting BST. How did you solve this?

### Insertion

First, a node is inserted while maintaining the characteristics of BST. Then, the color of the inserted node is set to RED. The reason for designating it as red is to minimize the change of Black-Height. As a result of the insertion, if the RBT characteristic is in violation, the color of the node is adjusted. If the Black-Height is violated, the height is adjusted through rotation. Through this process, the black-height of the internal nodes existing at the same height of the RBT becomes the same, and the size ratio of the minimum path and the maximum path is maintained below 2.

### Delete

Like insertion, deletion also deletes the corresponding node while maintaining the characteristics of BST. The rotation method varies depending on the number of children of the node to be deleted. And, if the color of the deleted node is Black, rotate so that 1 black node is added to the path where the Black-Height decreases by 1, and adjust the color of the node. If the color of the deleted node is red, no Violation occurs, so RBT is maintained.

> ArrayList in Java Collection is also internally composed of RBT, and is also used in Separate Chaining in HashMap. It is an important data structure with good efficiency.

</br>

[Back](https://github.com/jojo-tey/Today_I_Learned)/[Top](#Data-Structure)

## Hash Table

Since `hash` internally stores data using `array`, it has a fast search speed. When searching for a specific value, the time complexity is O(1) for the average case because the data's own `index' is accessed. However, the problem is that the `key` value stored in this index is irregular.

So, using a **special algorithm**, we create a unique number associated with the data to be stored and use it as an index. Since the index where specific data is stored is a unique location of the data, there is no need to intervene between other data during an insert operation or fill it with other data when deleting, so there is no additional cost in the operation.

</br>

### Hash Function

It seems important to set a unique index value through a'special algorithm'. The'special algorithm' mentioned above is called `hash method` or `hash function`, and the unique numeric value of the data returned by this method is called `hashcode`. It changes key values of saved values into **small range values** through `hash function`.

However, the same value can be derived if key values are determined through a clumsy `hash function'. In this case, multiple data with the same key value can exist in one table, which is called `Collision`.

</br>

> Collision: If two different keys are hashed with the same index, they cannot be stored in the same place.

#### So, what conditions should a good `hash function' have?

In general, a good `hash function' does not refer to a part of a key to create a hash value, but instead refers to the entire key to create a hash value. However, a good hash function depends on the characteristics of the key.

Rather than making the `hash function` unconditionally 1:1, it is more important to design in the direction of minimizing collision and how to respond to collisions that occur. It is almost impossible to make 1:1 correspondence, but when you create such a `hash function', it is no different from an array and takes up too much memory.

As the number of collisions increases, the time complexity required for search becomes closer to O(1) to O(n). The clumsy `hash function` prevents you from using hash as a hash. Choosing a good `hash function' is essential to improving the performance of the hash table.

Therefore, if the hashed index already contains different values, it can be saved only after finding another location to save the three data. Therefore, conflict resolution is essential, and let's see how to do it.

</br>

### Resolve Conflict

Remember two basic ways. There are more ways for solving hash collisions, but these are methods that apply the following two methods.

#### 1. Open Address

When a hash collision occurs (that is, if the hash bucket to be inserted is already in use), the method is to insert the data into another hash bucket. You can think of a bucket as a space for storing data in the same concept as a basket. What hash buckets do other hash buckets mean?

Also called public addressing, this algorithm wanders to find a place to store data when a collision occurs. In the case of the Worst Case, an empty bucket may not be found, and the search may be returned to the starting position. There are several methods in this process as well, but let's look at the following three.

1. Linear Probing
   It searches sequentially and continues until an empty bucket is found.
2. Quadratic probing
   Find a location to search using a quadratic function.
3. Double hashing probing
   When a collision occurs in one hash function, a new address is allocated using the second hash function. Compared to the above two methods, it requires a large amount of computation.

</br>

#### 2. Separate Chaining

In general, Open Addressing is slower than Separate Chaining. In the case of open addressing, the higher the density of filling the hash bucket, the higher the frequency of occurrence of the worst case. On the other hand, in the case of the Separate Chaining method, if it is possible to adjust through the auxiliary hash function so that hash collisions do not occur well, the frequency of approaching the Worst Case can be reduced. Java 7 implements HashMap by using the Separate Chaining method. There are two implementation methods for the Separate Chaining method.

- **Linked List**
  </br>
  This is a method of making each bucket into a linked list and adding it to the list of the bucket when a collision occurs. It inherits the characteristics of the linked list and is easy to delete or insert. However, when storing small data by inheriting the disadvantages, the overhead of the linked list itself becomes a burden. Another feature is that it can slow down the table expansion compared to the Open Address method, which uses buckets continuously.

- **Using Tree(Red-Black Tree)**
  </br>
  The basic algorithm is the same as the Separate Chaining method and uses a tree instead of a linked list. The criterion for whether to use a linked list or a tree is the number of key-value pairs assigned to one hash bucket. If the number of data is small, it is correct to use linked lists. This is because the tree basically uses a lot of memory. Looking at the Worst Case when the number of data is small, there is little difference in performance between the tree and the linked list. So, in terms of memory, when the number of data is small, a linked list is used.

**How little does it mean to have less data?**
</br>
As mentioned earlier, the criterion is the number of key-value pairs allocated to one hash bucket. The number of key-value pairs is determined based on six or eight. Having two standards can feel weird. Where did the 7 go? The criteria for the linked list and the tree are set to 6 and 8 in order to reduce the cost of making changes.

**Example**
</br>
There were **6** key-value pairs in the hash bucket. And one value was added. If the criteria are 6 and 7, the data structure must be changed from a linked list to a tree. Then, if one value is deleted immediately, you need to change the data structure from the tree to a linked list again. If the criterion for each data structure is 1, the switching cost is too high. That's why I set the standard with a margin of 2. Therefore, when the number of data increases from 6 to 7, it will take the data structure of the linked list, and when it decreases from 8 to 7, it will take the data structure of the tree.

#### `Open Address` vs `Separate Chaining`

First of all, both methods are O(M) in the Worst Case. However, because the `Open Address` method stores data in a contiguous space, the cache efficiency is higher than that of `Separate Chaining`. Therefore, if the number of data is sufficiently small, the `Open Address` method has better performance than `Separate Chaining`. There is one more difference. Compared to the `Separate Chaining` method, the `Open Address` method continues to use the bucket. Therefore, the `Separate Chaining` method can slow the expansion of the table.

#### Supplement hash function

The purpose of is to reduce the possibility of hash collisions by modifying the hash value of `key`. It is used together when the `Separate Chaining` method is used, and the case of getting close to the Worst Case can be reduced with a secondary hash function.

</br>

### Hash Bucket Dynamic Expansion(Resize)

If the number of hash buckets is small, memory usage can be saved, but performance loss occurs due to hash collisions. So, HashMap doubles the number of hash buckets when the number of key-value pair data exceeds a certain number. This increase can solve the problem of performance loss due to hash collision to some extent. In addition, an ambiguous expression'more than a certain number' appeared. The critical point for doubling the hash bucket size is when the current number of data becomes 75% of the number of hash buckets. The number `0.75` is called the load factor.

</br>

[Back](https://github.com/jojo-tey/Today_I_Learned)/[Top](#Data-Structure)

## Graph

### Set of vertices and edges, Graph

_Tree is also a graph, of which cycles are not allowed._

### Terms of Graph

#### Undirected Graph & Directed Graph (Digraph)

Literally, a graph that has no direction in the connection relationship between the vertex and the trunk is called Undirected Graph
A graph that includes directions on the edge is called a directed graph.

- Directed Graph (Digraph)

```
V = {1, 2, 3, 4, 5, 6}
E = {(1, 4), (2,1), (3, 4), (3, 4), (5, 6)}
(u, v) = the edge vertex u to vertex v
```

- Undirected Graph

```
V = {1, 2, 3, 4, 5, 6}
E = {(1, 4), (2,1), (3, 4), (3, 4), (5, 6)}
(u, v) = edge to vertex u and vertex v
```

#### Degree

The number of edges connected to each vertex in the undirected graph is called degree.
In Directed Graph, the degree is divided into two because there is a directionality in the trunk line.
The number of edges outgoing from each vertex is called Outdegree, and the number of incoming edges is called Indegree

#### Weight Graph & Sub Graph

The weight graph refers to a graph composed by placing weight information on an edge. The opposite concept is a non-weighted graph, that is, a graph in which all edges have the same weight. A similar concept to subsets is called fractional graphs. A partial graph is a graph consisting of some vertices and edges of the original graph.

</br>

### Two ways to implement the graph

#### adjacent matrix

The connection relationship between vertices can be identified as O(1) through the value of the corresponding location. Regardless of the number of edges, it has a space complexity of V^2. This is an appropriate method when expressing a density graph.

#### adjacent list

Since you have to check the adjacent list of vertices, it takes a long time to check whether the vertices are connected. Space Complexity is O(E + V). It is a suitable method for expressing a sparse graph.

</br>

### Graph search

In graphs, navigation is complicated because there are no rules for not only the composition of the vertices but also the connection of the edges. Therefore, the method to search all vertices of the graph is based on the following two algorithms.

#### Depth First Search: DFS

First, the method of advancing from one vertex in the graph to one connected vertex is first searched. It is to search through the connected vertices. We'll keep connecting until we have a vertex that we can connect to, and if there are no more connected vertices, we'll have to go back to the previous vertex and see if we can connect. You just need to organize it like a maze where there is a situation that returns the way you went. Which data structure should you use? It is the Stack.
</br>

**Time Complexity: O(V+E)… Number of vertices + number of edges**

#### Breadth First Search: BFS

Advances from any one vertex on the graph to all connected vertices. It is proceeded in the form of Level Order Traversal in Tree. BFS uses Queue as a data structure. This is to record the order of the vertices to be contacted.
First, the vertex that starts the search is put in the queue (enqueue), and while dequeueing, the dequeue vertices and the vertices connected by the edges are enqueued.
That is, vertices are stored in the queue in the order they are visited.
</br>

**Time Complexity : O(V+E) … number of vertex + number of edge**
_**! BFS 로 구한 경로는 최단 경로이다.**_

</br>

### Minimum Spanning Tree

It refers to a `spanning tree` in which the sum of edge weights is the minimum among spanning trees of graph G. The'spanning tree' here refers to a form in which all vertices of graph G are connected without cycles.

### Kruskal Algorithm

As an initialization operation, a graph is constructed with only vertices **without edges**. Then, examine the edge with the smallest weight. To do this, the Edge Set must be sorted non-decreasing. And the edge corresponding to the smallest weight is added, but only when there is no cycle in the graph when adding. When the spanning tree is completed, all vertices are connected and terminated. For a graph that cannot be completed, it is terminated when judgment is made for all edges.

#### How to determine whether to create a cycle?

An additional `set-id` is added to each vertex of the graph. And during the initialization process, each vertex is initialized with values ranging from 1 to n. Here, 0 means that no edge is connected. And each time it is connected, the `set-id` is unified into one, and the `set-id` value with the same number of `set-id` is unified.

#### Time Complexity

1. Sorting based on edge weight-O(E log E)
2. Check cycle creation and unify set-id-O(E + V log V)
   => Total time complexity: O(E log E)

### Prim Algorithm

During the initialization process, an initial graph A consisting of one vertex is constructed. Then, the edge between the vertices inside the graph A and the vertices outside are connected, and the vertex that is connected through the edge of the smallest weight is added. Regardless of which vertex, it is connected based on the weight of the edge. This connected vertex is included in graph A. Repeat the above process and finish when all vertices are connected.

#### Time Complexity

=> Total time complexity: O(E log V)

</br>

[Back](https://github.com/jojo-tey/Today_I_Learned)/[Top](#Data-Structure)






_Data structure.end_
