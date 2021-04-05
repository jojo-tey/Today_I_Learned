# Algorithm

- [Algorithm](#algorithm)
  - [Tips for Coding Interview](#tips-for-coding-interview)
    - [1. Start writing on the board.](#1-start-writing-on-the-board)
    - [2. Talk through it.](#2-talk-through-it)
    - [3. Think of an algorithm.](#3-think-of-an-algorithm)
    - [4. Think of the data structure.](#4-think-of-the-data-structure)
    - [5. Think about the related problems you saw before and how to fix them.](#5-think-about-the-related-problems-you-saw-before-and-how-to-fix-them)
    - [6. Break the problem down into smaller ones and fix them.](#6-break-the-problem-down-into-smaller-ones-and-fix-them)
    - [7. Don't be afraid to come back.](#7-dont-be-afraid-to-come-back)
  - [Interview Questions for Algorithms](#interview-questions-for-algorithms)
  - [Coding exercises](#coding-exercises)
  - [Strategic Approach to Problem Solving](#strategic-approach-to-problem-solving)
    - [Purpose of coding interview](#purpose-of-coding-interview)
    - [access](#access)
    - [When you think](#when-you-think)
  - [Theory](#theory)
    - [Array](#array)
      - [List / Tuple](#list--tuple)
    - [Stack](#stack)
    - [Queue](#queue)
    - [Hash Table](#hash-table)
    - [Sort](#sort)
      - [Selection sort](#selection-sort)
        - [Implement](#implement)
        - [Complexity](#complexity)
      - [Insertion sort](#insertion-sort)
        - [Implement](#implement-1)
        - [Complexity](#complexity-1)
      - [Bubble sort](#bubble-sort)
        - [Implement](#implement-2)
        - [Complexity](#complexity-2)
      - [Merge sort](#merge-sort)
        - [Implement](#implement-3)
        - [Complexity](#complexity-3)
      - [Heap sort](#heap-sort)
        - [Implement](#implement-4)
      - [Quick sort](#quick-sort)
        - [Implement](#implement-5)
        - [Complexity](#complexity-4)
    - [Tree](#tree)
      - [BST (Binary Search Tree)](#bst-binary-search-tree)
        - [Implement](#implement-6)
      - [Tree traversal algorithm](#tree-traversal-algorithm)
      - [Heap](#heap)
        - [Implement](#implement-7)
      - [Priority queue](#priority-queue)
    - [Graph](#graph)
      - [Direction graph](#direction-graph)
      - [Non-Direction graph](#non-direction-graph)
      - [Adjacency matrix](#adjacency-matrix)
      - [Adjacency list](#adjacency-list)
      - [Graph traversal](#graph-traversal)
        - [Depth-first search(DFS)](#depth-first-searchdfs)
        - [Breadth-first search(BFS)](#breadth-first-searchbfs)
  - [Search algorithm](#search-algorithm)
  - [Greedy Algorithm](#greedy-algorithm)
    - [Example 1](#example-1)
    - [Example 2](#example-2)
    - [Example 3](#example-3)
  - [Recursive algorithm](#recursive-algorithm)
  
  - String search
  - Shortest distance algorithm
  - Backtracking
  - Dynamic Programming
  - Division and conquest



---

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)

## Tips for Coding Interview

### 1. Start writing on the board.

This may sound obvious, but there are dozens of candidates stuck looking at the blank wall. I find it more productive to stare at an example of a problem than to see nothing. If you can think of a picture that is relevant, draw it. If you have a medium sized example, you can work. (Medium size is better than small one.) Because sometimes solutions for small examples are not generalized. Or write down a few propositions you know. Doing something is better than doing nothing.

### 2. Talk through it.

Don't worry if what you said might sound silly. Many people prefer to think quietly about a problem, but if you get stuck in solving a problem, talking can be one way. Sometimes speaking clearly to the interviewer about your progress can give you an opportunity to understand what's going on in a problem right now. Your interviewer may interfere with you to pursue that idea. Whatever you do, don't try to trick the interviewer for hints. If you need a hint, ask honestly.

### 3. Think of an algorithm.

Sometimes it's useful to go through the details of the problem and expect a solution to come up to you (this will be a bottom-up approach). However, you can also think about other algorithms and ask if each one applies to the problem in front of you (top-down approach). Changing the reference frame in this way can often give you immediate insight. Here are some algorithmic techniques that can help you solve more than half of the problems your interview requires.

- Sorting (plus searching / binary search)
- Divide and Conquer
- Dynamic Programming / Memoization
- Greediness
- Recursion
- Algorithms associated with a specific data structure (which brings us to our fourth suggestion...)

### 4. Think of the data structure.

Did you know that the top 10 data structures make up 99% of all data structures used in the real world? Sometimes the optimal solution asks you the problem of requiring a bloom filter or suffix tree. However, even these problems tend to use optimal solutions that use much more routine data structures. Here are the data structures you will most often see:

- Array
- Stack / Queue
- HashSet / HashMap / HashTable / Dictionary
- Tree / Binary tree
- Heap
- Graph

### 5. Think about the related problems you saw before and how to fix them.

The problem I have presented to you is the one you have seen before, or at least a little similar. Think about these solutions and think about how you can adapt to the details of the problem. Do not fall in the form of raising the problem. Move on to the core task and see if it matches what you have solved in the past.

### 6. Break the problem down into smaller ones and fix them.

Solve a special case or a simplified version of the problem. Looking at the corner cases is a great way to limit the complexity and scope of a problem. By reducing the problem to a subset of the larger problem, you can start with small parts and work through the whole range. It can also be helpful to see the problem as a composition of small problems.

### 7. Don't be afraid to come back.

If you feel that certain approaches are not working, there are times when you try different approaches. Of course, you shouldn't give up too easily. But, if you've spent a few minutes on a non-promising approach without bearing fruit, then back up and try something else. I have seen a lot of applicants who have progressed far more than those with less access. This means that others (all equal) have to give up the more agile approach.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)



## Interview Questions for Algorithms
* [Comprehensive list of interview questions of top tech companies](https://github.com/rishabh115/Interview-Questions)
* [A great list of Java interview questions](http://java2novice.com/java-interview-programs/)
* [Algorithms playground for common interview questions written in Ruby](https://github.com/sagivo/algorithms)
* [EKAlgorithms contains some well known CS algorithms & data structures](https://github.com/EvgenyKarkan/EKAlgorithms)
* [Five programming problems every Software Engineer should be able to solve in less than 1 hour](http://www.shiftedup.com/2015/05/07/five-programming-problems-every-software-engineer-should-be-able-to-solve-in-less-than-1-hour)
* [Top 10 Algorithms for Coding Interview](http://www.programcreek.com/2012/11/top-10-algorithms-for-coding-interview/)
* [Top 15 Data Structures and Algorithm Interview Questions for Java programmer](http://javarevisited.blogspot.com.by/2013/03/top-15-data-structures-algorithm-interview-questions-answers-java-programming.html)
* [Top Algorithms Questions by Topics](https://github.com/yangshun/tech-interview-handbook/blob/master/algorithms/README.md)
* [Daily Coding Interview Practice](https://www.techseries.dev/daily)

<br>

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)

<br>

## Coding exercises

* [Common interview questions and puzzles solved in a number of languages](https://github.com/mre/the-coding-interview)
* [Interactive, test-driven Python coding challenges (algorithms and data structures) typically found in coding interviews or coding competitions](https://github.com/donnemartin/interactive-coding-challenges)
* [Interview questions solved in python](https://github.com/roseperrone/interview-questions)
* [7 Swift Coding Challenges to Practice Your Skills](https://www.makeuseof.com/tag/swift-coding-challenges/)


## Strategic Approach to Problem Solving

### Purpose of coding interview

1. Whether to solve the problem
2. Exception and threshold handling
3. Code quality, including code readability and redundancy
4. Language understanding
5. Efficiency

Ultimately, it is to measure problem-solving ability, and it can be seen as to measure'how to creatively solve this problem'.

### access

1. The priority is to take the problem aggressively and request additional necessary information so that you have a complete understanding of the problem.
2. Redefine the problem in familiar terms or extract information to solve the problem. This process is called abstraction.
3. Plan how to solve this problem based on abstracted data. Consider the algorithm and data structure to use at this time.
4. Verify the plan you have made. It may be applicable to writing code, and you can ask the questioner for comments.
5. Try to solve the problem with the plan you have made. If that doesn't work, review the previous process.

### When you think

- Think of a similar problem.
- Start with a simple method and improve gradually.
- Think of a small value.
- Draw with a picture.
- Express it with a formula.
- Try to force the order.
- Think from the back.

</br>

<br>

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)

<br>

---

<br>

## Theory

<br>

### Array

If you use an array, you can group and use separately scattered variables into one, so you can write code efficiently. An object is stored in an array, and the stored object is called an element. Also, each element has an index starting from 0. When creating an array, you can freely specify the number of elements.
Also, arrays can have different data types.


#### List / Tuple

In Python, arrays can be implemented as lists and tuples. Lists and tuples are similar, but differ depending on whether or not the elements are mutable.

> mutable: list, dictionary, set, etc. (value can be changed)
> immutable: numbers, strings, tuples, etc. (value cannot be changed)


Using lists, we can simply express a collection of numbers 1, 3, 5, 7, and 9 as follows:

```py
>>> odd = [1, 3, 5, 7, 9]
```

When creating a list, wrap it in square brackets ([ ]) as shown above, and separate the minimum values with a comma (,).

List name = [Element 1, Element 2, Element 3, ...]
Looking at the appearance of various lists are as follows.

```py
>>> a = []
>>> b = [1, 2, 3]
>>> c = ['Life', 'is', 'too', 'short']
>>> d = [1, 2, 'Life', 'is']
>>> e = [1, 2, ['Life', 'is']]
```


A list can be an empty list ([ ]) containing nothing like a, a number as a minimum value, like b, or a string like c, as a minimum value. Also, like d, you can have both a number and a string as a minimum value, and like e, you can have a list itself as a minimum value. That is, any data type can be included in the list.



- Linear list


Linear lists, also known as ordered lists, are one of two types of lists.

The size of the `list` is set statically from the beginning, so the number of data is also limited `fixed`.

 

It is mainly implemented as an `fixed size` array.

So there is an order between the elements, and you can use an index for each element.

So, it's efficient for searching for elements `directly referred to as index`, but inefficient for inserting and deleting elements. `In one delete, insert, worst case, all existing data must be moved`

There are two cases in inserting a linear list.

The question is whether there is already a value at the insert position `index` If the location to insert is an empty space with no value, you can insert the element immediately.

 

If there is already another value at the insert position, you must push the original value one space back to insert the new value while keeping the original value. `It moves the value to the next index of the existing index`

But what if another value already exists in the location to be moved? Therefore, it should be done as if pushing the last element one by one from the insert position.


Deleting from the linear list is the opposite.

It is okay to delete the last element, but if it is not the last element, there will be an empty space in the middle of the list after deletion.

If so...

The elements after the index to be deleted must be moved one space to the front so that the empty space can be filled again.
Often, inserting and deleting a linear list is easy when you think of standing in a row.


- Linked list 

The linked list consists of several nodes. Each node has data and an address that tells what the next node is. Also, linked lists should have the ability to add new data, locate or remove data.

If there is a linked list of 1->2->3->4->5, 1,2,3,4,5 are data and -> are addresses. Unfortunately, this is already implemented in JavaScript. It's an array. If there is [1,2,3,4,5], 1,2,3,4,5 are data, and array[0], array[1], etc. tells the location of the data. Also, data can be added through array.push(); and data can be removed through array.splice();.

LinkedList has length and head. length is the part that expresses the number of nodes, and head is the part that indicates the address of the first node.

There is also a special linked list. The default linked list moves in only one direction. So it's inconvenient to go back again. The list that solved this is a double linked list. In addition to next, I put this.prev to point to the previous node. The implementation gets a little more complicated, but once implemented, you can conveniently move back and forth between nodes afterwards. There are also multiple linked lists that connect only one data at a time, but connect multiple nodes from one node.




### Stack


Stack is one of the data structures that are often used in real life. It's a linked list, but you can put it back and subtract it only. In the future, I cannot put it in or take it out. In simple terms, it's a JavaScript array, but you can think of it as push and pop without shift or unshift. In fact, the method names push and pop came from the stack. Another method is to tell stackTop the last element of the stack. The last element of the stack is sometimes called top.

In real life, it would be comfortable to think of the plates stacked up and down in the kitchen. Put a new plate on top, and when using a plate, take it out from the top Stacks are also often used in programming. Have you ever heard of a stack overflow or stack underflow? Stack overflow is also a popular overseas programming question-and-answer community. This is a typical error that occurs when more data is put in each given stack memory or when the stack memory is empty and you try to retrieve data from there. When you accidentally call a recursive function infinitely, a stack overflow occurs.

What does a stack overflow have to do with calling a recursive function? This is because calling a function in succession pushes it into memory like a stack. They are executed one by one (pop) in reverse stacked order. Even if it is not a recursive function, when multiple functions are called by nesting, they are stacked like a stack. However, stack overflow errors often occur when recursive functions are used.

```py


stack = [1,2,3]
stack.append(4)

>>> stack 
# [1, 2, 3, 4]

top = stack.pop()
 
>>> print(top)
>>> stack
 
# 3
# [1, 2]
```

```js

var Stack = (function() {
  function Stack() {
    this.top = null;
    this.count = 0;
  }
  function Node(data) {
    this.data = data;
    this.next = null;
  }
  Stack.prototype.push = function(data) {
    var node = new Node(data);
    node.next = this.top;
    this.top = node;
    return ++this.count;
  };
  Stack.prototype.pop = function() {
    if (!this.top) { // avoid stack underflow 
      return false;
    }
    var data = this.top.data;
    this.top = this.top.next;
    // clean memory for this.top
    this.count--;
    return data;
  };
  Stack.prototype.stackTop = function() {
    return this.top.data;
  };
  return Stack;
})();


var stack = new Stack();
stack.push(1); // 1
stack.push(3); // 2
stack.push(5); // 3
stack.pop(); // 5
stack.stackTop(); // 3
```


[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)

<br>

### Queue

You can think of cues as shortening in real life. Wait in line when we wait for the order, right? The newcomer stands at the end of the line, and the first person takes the necessary action and then leaves. This is a structure that enqueues from the back and dequeue from the front. In terms of JavaScript arrays, you can think of it as having only push(enqueue) and shift(dequeue) methods. In addition, there is a front where you can see the front data.

If the stack had only top pointing to the top, the cue has two heads pointing to the very beginning and rear pointing to the far end.

There are also special cues. The circular queue is one of them. The front and rear are connected. For example, when there is a queue that contains data of 1, 2, and 3, it ends at 3 if it was originally, but the circular queue moves from 3 at the rear to 1 at the front. Coding can be implemented by simply adding this.rear.next = this.front. The reason the circular queue is used is because it is easy to manage memory, but it is a little less useful because JavaScript organizes the memory on its own.

Another queue is the priority queue. The enqueue and dequeue are the same, but the data is put in order of priority rather than putting it at the end when enqueueing. It is up to the programmer to decide which data has the highest priority. The problem is that the priority queue has the disadvantage that it is difficult to insert data if it is implemented as a queue as above. So, it is mainly obtained by using a data structure called heap.



- Using Queue in python


1. Deque in the collections module stands for double-ended queue, a data structure that allows data to be added and removed in both directions. The disadvantage is that the time complexity of random access is O(N). This is because it uses a linked list internally, and it takes i iterations from the front/back to access the i-th data.

2. Another way is to use the queue module's Queue class. This method is mainly used in a multi-threading environment, and it supports locking internally so that multiple threads can add or delete data at the same time. Unlike deque, since there is no direction, data addition and deletion are handled in one method. So, to add data, use the put(x) method, and to delete data use the get() method.


```python




>>> from collections import deque
>>>
>>> queue = deque([4, 5, 6])
>>> queue.append(7)
>>> queue.append(8)
>>> queue
deque([4, 5, 6, 7, 8])
>>> queue.popleft()
4
>>> queue.popleft()
5
>>> queue
deque([6, 7, 8])


>>> from collections import deque
>>>
>>> queue = deque([4, 5, 6])
>>> queue.appendleft(3)
>>> queue.appendleft(2)
>>> queue
deque([2, 3, 4, 5, 6])
>>> queue.pop()
6
>>> queue.pop()
5
>>> queue
deque([2, 3, 4])



>>> from queue import Queue
>>>
>>> que = Queue()
>>> que.put(4)
>>> que.put(5)
>>> que.put(6)
>>> que.get()
4
>>> que.get()
5
>>> que.get()
6
```

```js

var Queue = (function() {
  function Queue() {
    this.count = 0;
    this.head = null;
    this.rear = null;
  }
  function Node(data) {
    this.data = data;
    this.next = null;
  }
  Queue.prototype.enqueue = function(data) {
    var node = new Node(data);
    if (!this.head) {
      this.head = node;
    } else {
      this.rear.next = node;
    }
    this.rear = node;
    return ++this.count;
  };
  Queue.prototype.dequeue = function() {
    if (!this.head) { // avoid stack underflow 
      return false;
    }
    var data = this.head.data;
    this.head = this.head.next;
    // clean memory for this.head 
    --this.count;
    return data;
  };
  Queue.prototype.front = function() {
    return this.head && this.head.data;
  };
  return Queue;
})();


var queue = new Queue();
queue.enqueue(1); // 1
queue.enqueue(3); // 2
queue.enqueue(5); // 3
queue.dequeue(); // 1
queue.front(); // 3

```

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)

### Hash Table

- What is Hash Table? 

A hash table is one of the data structures that store data as (Key, Value), and is a data structure that allows you to quickly search for data. The reason why hash tables provide fast search speed is that data is stored internally using arrays (buckets). The hash table creates a unique index of the array by applying a hash function to each key value, and stores or retrieves the value using this index. Here, the place where the actual value is stored is called a bucket or slot.


For example, suppose we store data with (Key, Value) of ("John Smith", "521-1234") in a hash table of size 16. Then, index = hash_function("John Smith")% 16 is calculated to calculate the index value. And it stores the phone number as array[index] = "521-1234".

When data is stored in this structure, it is possible to save/delete/retrieve data very quickly because it is necessary to execute the hash function only once when searching for data by key value. The average time complexity of the hash table is O(1).

<br>

- Hash Function (Hash Function)

The important thing in the hash function is to set a unique index value. There are three typical hash functions used in the hash table as follows.

Division Method: Calculates the input value by dividing the input value by the size of the table by using division. (Address = input value% size of the table) It is known that the effect is good when the size of the table is set to a decimal number and a power of 2 and a far value are used.

Digit Folding: This is a method of converting the character string of each key into ASCII code and using the summed data as an address in the table.

Multiplication Method: Using the numeric key value K and the real number A between 0 and 1, and m, which is usually a power of 2, the following calculation is performed. h(k)=(kAmod1) × m

Univeral Hashing: This is a technique that creates a hash value by creating a number of hash functions and putting them in set H, and randomly selecting a hash function.



[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)


### Sort

#### Selection sort


[Select sort Explain-Video](https://youtu.be/Ns4TPTC8whw)


Selective sorting is a sorting algorithm that can be easily conceived by anyone who has never learned about it. That's because it's a common way of thinking in our daily lives when we list things in order of size.<br>
Selection sort fills the sorted values ​​one by one from the beginning of the array. Therefore, it has the characteristic that the comparison range gradually decreases one by one as it goes to the back index. (At index 0, you need to compare from 0 to n-1, but at index n-1, there is only one remaining number, so no comparison is necessary.)<br>
Regardless of whether the input array is already sorted or not, it has the same amount of computation, so the optimization excitation is small, so performance tends to be poor even compared to other O(N^2).

> Because of these performance limitations, it is hardly seen in practice, but it is the easiest sorting algorithm to implement, so it is a popular sorting algorithm that you come across once in class.


`170cm, 180cm, 150cm, 160cm`

For example, as shown above, to set up four friends who know their height in order of height, first compare the heights of all four and place the friend whose height is the smallest 150cm in front.<br>

The friend, who is 150cm tall, was placed first. Now, compare the height of the other three friends and put the friend whose height is the smallest 160cm next. Now there are only two friends left, one 170cm tall and one 180cm tall. Of the two, the 170cm friend is smaller, so this friend is established first, and then the 180cm friend last.



Index | Value 
------------ | ------------- 
0 | Smallest of all values
1 | The smallest value among the remaining values excluding the first value (Index=0)
... | ...
i | The smallest of the values from i to n-1
n-2	| The smallest of the n-2th and n-1th values
n-1	| One last value (no comparison)

<br>

That is, given an array of size n, for all index i from index 0 to n-1, if you find the smallest value among the values from i to n-1 and place it at index i, you can get a sorted array. There is. This sorting algorithm is called "Selection Sort" or "Selection Sort" because it "selects" the value to be placed at that index for all indexes.


##### Implement

You need two loops. In the inner loop, the index of the minimum value from the current index to the last index is found, and in the outer loop, the index of this minimum value and the value at the current index are swapped. In the outer loop, index i is progressed from 0 to n-2 (or n-1. Since there is only one remaining value in the last index, there is no problem with the trend), and index j is not interested in the values already sorted in the inner loop. Progresses from i to n-1. To find the minimum value for each index, case comparisons occur multiple times, but the swap is known only once.



```python
def selection_sort(arr):
    for i in range(len(arr) - 1):
        min_idx = i
        for j in range(i + 1, len(arr)):
            if arr[j] < arr[min_idx]:
                min_idx = j
        arr[i], arr[min_idx] = arr[min_idx], arr[i]

# Other Example

input = [5, 10, 66, 77, 54, 32, 11, 13]
sorted_list = []

while input:
  sorted_list.append(min(input))
  input.pop(input.index(min(input)))

print(sorted_list)

```

##### Complexity

1. Selection sort has a spatial complexity of O(1) because it only changes the position of values within the space occupied by a given array without using extra space.
2. Time complexity basically consumes O(N) time because all indexes must be accessed through a loop statement. In one loop, the current index value is compared with the values of other indexes to find the minimum value. O(N) time is required because we have to swap the values in the index. Therefore, selective sorting is a sorting algorithm with a total time complexity of O(N^2).

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)

#### Insertion sort


[Insert sort Explain-Video](https://youtu.be/ROalU379l3U)


Insertion sort, expressed in a word, is an algorithm that expands the sort range by one space and compares the newly entered values with the existing values and selects them in the proper place.
The selection/bubble alignment decreases the search range as the passes pass, while the insertion alignment gradually increases the alignment range.
Looking at the big cream, the outer loop is going forward and the inner loop is going backwards. <br>


For example, let's say you have an array containing a total of 5 numbers from 1 to 5.

```
[2, 1, 5, 4, 3]
```

At first, let's just consider the first two values to be included in the sort range. The leading value 2 is less than the trailing value 1, so they swap places.

```
[2, 1]: 2 > 1 => swap
 ^  ^
[1, 2]
 *  *
```

Next, consider adding a third value by expanding the existing sort range by one space. If you compare the new 5 with the largest value of 2 in the existing sort range, you can see that there is no need to change places. There is no need to compare 1 and 5 because the two values that were in the sorting range were already sorted in the previous pass.

```
[1, 2, 5]: 2 < 5 => OK
    ^  ^
[1, 2, 5]
 *  *  *
```

In the next pass, it's time to expand the sort range by one more space, add a fourth value, and think about it. If you compare the largest value of 5 in the existing sorting range with the newly added 4, the values in front must be swapped because the values in front are larger than values in the rear. Now, if you compare the 2nd largest value in the existing sorting range, 2, and 4, which has just been replaced, you can see that there is no need to change any more.

```
[1, 2, 5, 4]: 5 > 4 => swap
       ^  ^
[1, 2, 4, 5]: 2 < 4 => OK
    ^  ^
[1, 2, 4, 5]
 *  *  *  *
```

In the last pass, the sorting range is expanded all over to include the last value. If you compare the newly added value and the existing values from the back in the same way as you have done so far, you can see that two digit replacements are required.

```
[1, 2, 4, 5, 3]: 5 > 3 => swap
          ^  ^
[1, 2, 4, 3, 5]: 4 > 3 => swap
       ^  ^
[1, 2, 3, 4, 5]: 2 < 3 => OK
    ^  ^
[1, 2, 3, 4, 5]
 *  *  *  *  *
```

##### Implement

1. You need two loops. In the inner loop, the values newly added to the sort range and the existing values are compared from the back, and if the previous value is larger than the next value, a swap is performed. In the outer loop, the sort range is expanded from 2 to N.

```py
def insertion_sort(arr):
    for end in range(1, len(arr)):
        for i in range(end, 0, -1):
            if arr[i - 1] > arr[i]:
                arr[i - 1], arr[i] = arr[i], arr[i - 1]
```

2. By taking advantage of the fact that all existing values were sorted in the previous pass, unnecessary comparisons can be eliminated. For example, if 4 is newly added to the existing sort range [1, 2, 3, 5] as shown below, swap is required because 5 is greater than 4, but swap is not required because 3 is less than 4. And since the numbers before 3 are already sorted in the previous pass, they will of course be less than 3, and any further 4 and case comparisons are meaningless. Using this fact, you only have to run the inner loop until the first moment you encounter a number less than the newly added value. <br>

Applying this optimization, you can achieve a time complexity of O(N) when an ordered array comes in. For example, if you come in an array of 5 numbers like this, you can find out that the array is fully aligned and complete the insertion sort with only 4 comparisons, once per pass.


```py
def insertion_sort(arr):
    for end in range(1, len(arr)):
        i = end
        while i > 0 and arr[i - 1] > arr[i]:
            arr[i - 1], arr[i] = arr[i], arr[i - 1]
            i -= 1
```



3. Insertion sort can be implemented simply by shifting the values without the swap operation. If the previous value is greater than the value added to the sort range, you can push the previous value back and insert the added value the moment it first encounters the smaller value.

```py
def insertion_sort(arr):
    for end in range(1, len(arr)):
        to_insert = arr[end]
        i = end
        while i > 0 and arr[i - 1] > to_insert:
            arr[i] = arr[i - 1]
            i -= 1
        arr[i] = to_insert

```


##### Complexity

1. Insertion sort has a spatial complexity of O(1) because it only changes the position of values within the space occupied by a given array without using extra space.
2. As for time complexity, it is necessary to start with two sorting ranges through a loop statement and expand them to the whole, so basically O(N) is time consuming. You will need O(N) time to change seats. So, insert sort is a sorting algorithm with a total time complexity of O(N^2).
3. The optimizations covered below can significantly improve performance for partially ordered arrays, and can improve time complexity even up to O(N), especially when fully ordered arrays come in.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)


#### Bubble sort


[Bubble Sort Explain-Video](https://youtu.be/lyZQPjUT5B4)


Bubble alignment has a structure that aligns from the back to the front when viewed in the big picture. In other words, the largest value is sent to the back in the last digit, and the second largest value is sent immediately before the largest value. To do this, we need to constantly perform the task of comparing the values in the array back and forth and swapping places. Sending such a large value back and forth continuously looks like a bubble moving, so it has the name Bubble Alignment.<br>

First, let's look at how to send the largest value to the back through bubble sort. Start from the first value and compare them with the next values in order, and if the previous value is larger, you can change the position with the latter value.<br>

Let's apply the above logic to an array containing a total of 5 numbers from 1 to 5.

```
[4, 3, 5, 1, 2]
```
First, compare 4 and 3. Because 4 is greater than 3, we swap places.

```
[4, 3, 5, 1, 2]
 ^  ^
4 > 3 => Swap
[3, 4, 5, 1, 2]
```
Then compare 4 and 5. Since 4 is less than 5, there is no need to change places
```
[3, 4, 5, 1, 2]
    ^  ^
4 < 5 => No Swap
```
Then compare 5 and 1. Because 5 is greater than 1, we swap places.
```
[3, 4, 5, 1, 2]
       ^  ^
5 > 1 => Swap
[3, 4, 1, 5, 2]
```
Then compare 5 and 2. Because 5 is greater than 2, we swap places.

```
[3, 4, 1, 5, 2]
          ^  ^
5 > 2 => Swap
[3, 4, 1, 2, 5]
             *
```

In this way, it starts from the first value and continuously compares the case with the next value, and if the previous value is greater than the latter value, change the place, and eventually the largest value can be sent to the back.<br>

If you extend this process to all values, you can send the second largest value right before the largest value, and the third largest value before the second largest value like this:


```
Initial: [4, 3, 5, 1, 2]

 Pass 1: [3, 4, 1, 2, 5]
                      *
 Pass 2: [3, 1, 2, 4, 5]
                   *  *
 Pass 3: [1, 2, 3, 4, 5]
                *  *  *
 Pass 4: [1, 2, 3, 4, 5]
             *  *  *  *
 Pass 5: [1, 2, 3, 4, 5]
          *  *  *  *  *
```



-Bubble sorting accumulates larger values one by one from the back to the front, so the sorting range decreases one by one as you go to the second half.
-Because in the next pass, you can only compare until the position with the largest value sent back from the previous pass.
-It has the opposite sorting direction compared to the selection sort which finds the smallest value and places it at the front.
-Compared to other sorting algorithms, swaps tend to occur more frequently. For example, in the case of selection sort, the shift occurs only once in each pass.
-Algorithm with a lot of room for optimization For example, in the picture above, Pass 5 is a pass that can be omitted. This is because there has never been a seat shift in Pass 4.



##### Implement

As with the selection sort, it requires two loops. In the inner loop, the previous value is compared continuously from the first value to the position of the value sent back from the previous pass, and if the previous value is greater than the last value, a swap is performed. In the outer loop, the sorting range from back to front is reduced from n-1 to 1.

```py
def bubble_sort(arr):
    for i in range(len(arr) - 1, 0, -1):
        for j in range(i):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
```


If no swap has occurred in the previous pass, you can assume that none of the misaligned values have occurred. So in this case, you do not need to perform a subsequent pass.


```
Initial: [1, 2, 3, 5, 4]

 Pass 1: [1, 2, 3, 4, 5] => Swap
                      *
 Pass 2: [1, 2, 3, 4, 5] => No Swap
                   *  *
=> Since there was never any swap in the previous pass
``` 

```py
def bubble_sort(arr):
    for i in range(len(arr) - 1, 0, -1):
        swapped = False
        for j in range(i):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
                swapped = True
        if not swapped:
            break
```

Instead of checking whether there was a swap in the previous pass, you can remember the index where the last comparison was made, so you can sort only before that place in the next pass. Therefore, instead of reducing the sorting range by one space, you can reduce the sorting range by several spaces at a time.

```py
def bubble_sort(arr):
    end = len(arr) - 1
    while end > 0:
        last_swap = 0
        for i in range(end):
            if arr[i] > arr[i + 1]:
                arr[i], arr[i + 1] = arr[i + 1], arr[i]
                last_swap = i
        end = last_swap
```


##### Complexity

- Bubble sort has a spatial complexity of O(1) because it does not use extra space and only changes the position of values within the space occupied by a given array.
- Time complexity basically consumes O(N) time because all indices must be accessed through a loop statement from the back to the top. In one loop, O(N) is used for size comparison and shift of adjacent values. ) You will need time. Thus, bubble sort is a sorting algorithm with a total time complexity of O(N^2).
- However, bubble sorting can significantly improve performance by optimizing for partially ordered arrays, and when fully ordered arrays come in, even O(N) can increase time complexity.


[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)


#### Merge sort

[Merge sort Explain-Video](https://youtu.be/XaqR3G_NVoo)

Merge sort is a sorting algorithm using the Devide and Conquer technique and a recursive algorithm. In other words, the given array is split in two until there is only one element left, and then re-arranged in order of size, concatenating it into an array of the original size.<br>

For example, let's say you have an array containing 8 total numbers from 1 to 8.
```
[6, 5, 3, 1, 8, 7, 2, 4]
```
First, split an array into two.
```
[6, 5, 3, 1] [8, 7, 2, 4]
```
And again, split the two arrays into four.
```
[6, 5] [3, 1] [8, 7] [2, 4]

```
Finally, split the array of four dishes into eighty pieces.
```
[6] [5] [3] [1] [8] [7] [2] [4]
```
Now that I can't split it any more, I'm going to start combining them two by one. When concatenating, smaller numbers place the larger numbers in front and the back.
```
[5, 6] [1, 3] [7, 8] [2, 4]
```
Now combine the four arrays into two. If you compare the two smallest values in each array and select the smaller value first, the selection is naturally ordered by size.
```
[1, 3, 5, 6] [2, 4, 7, 8]
```
Finally, the two arrays can be sorted by selecting them in order of size and combining them into one.
```
[1, 2, 3, 4, 5, 6, 7, 8]
```


##### Implement

Merge sort can be implemented using recursion. First, divide the array as much as possible until it can no longer be divided (until there is only one element left), then merge again to create a larger array. Therefore, the basis condition of this recursive algorithm is when the size of the input array is less than 2, and when this condition is met, the array can be returned as it is. <br>


Using Python's list slice notation(arr[start:end]), you can write concise code like this: However, when the list is sliced, the memory usage efficiency is not good because the array is duplicated.

```py
def merge_sort(arr):
    if len(arr) < 2:
        return arr

    mid = len(arr) // 2
    low_arr = merge_sort(arr[:mid])
    high_arr = merge_sort(arr[mid:])

    merged_arr = []
    l = h = 0
    while l < len(low_arr) and h < len(high_arr):
        if low_arr[l] < high_arr[h]:
            merged_arr.append(low_arr[l])
            l += 1
        else:
            merged_arr.append(high_arr[h])
            h += 1
    merged_arr += low_arr[l:]
    merged_arr += high_arr[h:]
    return merged_arr
```

> Instead of creating and returning a new array to hold the merge result each time, memory usage can be drastically reduced by continuously updating the input array using index access. (In-place sort)

```py
def merge_sort(arr):
    def sort(low, high):
        if high - low < 2:
            return
        mid = (low + high) // 2
        sort(low, mid)
        sort(mid, high)
        merge(low, mid, high)

    def merge(low, mid, high):
        temp = []
        l, h = low, mid

        while l < mid and h < high:
            if arr[l] < arr[h]:
                temp.append(arr[l])
                l += 1
            else:
                temp.append(arr[h])
                h += 1

        while l < mid:
            temp.append(arr[l])
            l += 1
        while h < high:
            temp.append(arr[h])
            h += 1

        for i in range(low, high):
            arr[i] = temp[i - low]

    return sort(0, len(arr))


```

##### Complexity


- Looking at the algorithm in the big picture, it can be divided into a split step and a merge step, and the merge cost of comparing all values is higher than the split cost of simply finding an intermediate index.
- As shown in the example, O(logN) time is required because the total number of iterations gradually decreases in half with the equation 8 -> 4 -> 2 -> 1, and all values must be compared when merging in each pass. O(N) time is consumed. So the total time complexity is O(NlogN).
- When merging two arrays, an additional array is required to hold the merge result. So the spatial complexity is O(N).
- Unlike other sorting algorithms, no swap occurs between adjacent values.



[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)



#### Heap sort


[Heap sort Explain-Video](https://youtu.be/Xw2D9aJRBY4)


To know heap sorting, you first need to know what heap is.

The heap is a heap tree, which is a binary tree created to quickly find the largest or smallest value among multiple values. 

![heapsort](/images/heapsort.gif) 

The heap always takes the form of a full binary tree. There is a rule that the parent's value must always be greater (Max Heap) or less (Min Heap) than the child's value. Therefore, the largest or smallest value among data is always stored in the root node.<br>

The heap sort method is as follows.<br>

1. Insert all the elements of the array into the heap
2. Since the value in the most parent node is the maximum or minimum value, print the root and remove it from the heap.
3. Repeat step 2 until the heap is empty.

<br>

> Heap sorting has the advantage that it does not require any additional memory and always shows O(n log n) performance even in the worst case.


##### Implement

```py
def heapify(li, idx, n):
    l = idx * 2;
    r = idx * 2 + 1
    s_idx = idx
    if (l <= n and li[s_idx] > li[l]):
        s_idx = l
    if (r <= n and li[s_idx] > li[r]):
        s_idx = r
    if s_idx != idx:
        li[idx], li[s_idx] = li[s_idx], li[idx]
        return heapify(li, s_idx, n)
 
def heap_sort(v) :
    n = len(v)
    v = [0]+v
 
    # min heap 
    for i in range(n, 0, -1) :
        heapify(v, i, n)
 
    # min element extract & heap
    for i in range(n, 0, -1) :
        print(v[1])
        v[i], v[1] = v[1], v[i]
        heapify(v, 1, i-1)
 
heap_sort([5,3,4,2,1])


```

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)



#### Quick sort

Like merge sort, quick sort is a sorting algorithm using the Divide and Conquer technique and a recursive algorithm.

[Quick sort Explain-Video](https://youtu.be/ywWBy6J5gz8)

-Most of the built-in sorting functions that are basically supported at the programming language level, such as Python's list.sort() function and Java's Arrays.sort(), are based on quicksort.
-In general, as the number of elements decreases, the probability of selecting a bad intermediate value increases, so there are many cases where different sorts are mixed for quicksort depending on the number of elements.
-Merge sort and quick sort look similar in terms of using split-conquer and recursive algorithms, but there is a big difference in the way that sorting is done internally.
-Merge sort always performs a simple split based on the center and then compares values ​​at the time of merging, whereas in quick sort, the comparison operation takes place from the time of split, so the cost of subsequent merges is very low or depending on the implementation You may not merge them at all. <br>

For example, here is an array containing a total of 7 numbers from 1 to 7.

```
[6, 5, 1, 4, 7, 2, 3]
```
Unlike merge sort, which always splits around the center, quick sort uses an arbitrary reference value, often called a pivot. There are several ways to select a pivot value, but for simplicity, I will set the center 4 as the pivot for simplicity. And based on this pivot value, it is divided into groups with values less than pivot and groups with values greater than pivot, as follows:

```
            p
[3, 2, 1] < 4 < [7, 5, 6]
```
As above, if all values smaller than the pivot value are driven to the left, and all larger values are driven to the right, the reference value is placed in an exact aligned position. Also, if you divide it this way, you will no longer need to compare the values on the left and the values on the right in the future. Therefore, it is possible to sort the values after comparing only the values within the same side, whether on the left or the right, without paying attention to the opposite side at all.

First, let's align the left side in the same way. The pivot value located in the middle of the left is 1, which is less than 2, and the larger value of 3 is on the right. Now that both sides only have one value, this completes the left-hand alignment.
```
      p
[1] < 2 < [3]
```

Let's align the right side in the same way. There is no value less than 5, which is the pivot value on the right, so I placed both 7 and 6 on the right.
```
    p
[] < 5 < [7, 6]
```

There are 2 values on the right (?) on the right, so additional alignment is required. Since there are no values on the left, but there are still two values on the right, we will apply the same sorting.

```
      p
[6] < 7 < []
```
Finally, if you combine all the values that have been split left and right so far, you can get the sorted array as follows.
```
[1, 2, 3, 4, 5, 6, 7]
```
As we have seen so far, quicksort takes a method of sorting by repetitively dividing the array into smaller and larger values based on the pivot value.


##### Implement

The basic concept described above can be implemented as it is in code. First, we select the value in the middle of the list as the pivot value, and we create three lists to hold the value less than the pivot value, the same value, and the larger value. Then, each value is added to the corresponding list after comparison with the pivot through a loop. Then we call the quicksort function recursively on an array containing small and large values. Finally, sum the results of the recursive call back in order of size to get a sorted list.

```py
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    lesser_arr, equal_arr, greater_arr = [], [], []
    for num in arr:
        if num < pivot:
            lesser_arr.append(num)
        elif num > pivot:
            greater_arr.append(num)
        else:
            equal_arr.append(num)
    return quick_sort(lesser_arr) + equal_arr + quick_sort(greater_arr)
```
The above implementation is concise and easy to understand, but it is inefficient in terms of memory usage because it creates and returns a new list each time it is called recursively. In commercial code that has to deal with large input data, this drawback can be fatal, so in-place sorting with less extra memory is preferred.

> Writing code that implements in-place sorting yourself from scratch may not be as easy as you might think. This is because the pivot value is used for the comparison of the values as before, but the reference point for partitioning may not be a pivot value. This is because, when comparing the size based on the pivot value, it is rare that the free space on the left and right is just right.

```py
# The main function quick_sort() is largely divided into two internal functions, sort() and partition(). The sort() function is a recursive function and takes a sort range as arguments as a starting index and an ending index. (Both inclusive) The partition() function takes a sort range as an argument, sorts the left and right values according to the following logic and returns the index of the partition base point. This splitting point (mid) is used as the starting index of the list on the right when sort() is called recursively.

def quick_sort(arr):
    def sort(low, high):
        if high <= low:
            return

        mid = partition(low, high)
        sort(low, mid - 1)
        sort(mid, high)

    def partition(low, high):
        pivot = arr[(low + high) // 2]
        while low <= high:
            while arr[low] < pivot:
                low += 1
            while arr[high] > pivot:
                high -= 1
            if low <= high:
                arr[low], arr[high] = arr[high], arr[low]
                low, high = low + 1, high - 1
        return low

    return sort(0, len(arr) - 1)

```


##### Complexity

- The performance of quicksort can vary greatly depending on how you choose the pivot value. In the ideal case, the same number of small values ​​and large values ​​are divided based on the pivot value, resulting in a time complexity of O (NlogN) like merge sort.
- However, if the values ​​are largely skewed to one side when dividing based on the pivot value, the performance of the quicksort will deteriorate, and in the worst case, all values ​​will be concentrated on only one side, thus reducing the time complexity of O(N^2). Will be visible.
- Therefore, in commercial code, a delicate strategy to select a pivot value that is close to the median is required, and the method of using the medium sized value among the first, median, and last values ​​of the array is often used.
- The space complexity of quick sort can vary depending on the implementation method. If the implementation is used in an in-place sorting method that uses only the memory occupied by the input array, it is possible to implement a code with a space complexity of O(1).

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)




### Tree

#### BST (Binary Search Tree)

Before we get into the binary search tree, let's take a quick look at the binary tree. A binary tree is a tree type and refers to a tree in which each node has at most two child nodes. That is, each node of the binary tree may not have child nodes, and may have one or two.<br>

A binary search tree is a tree arranged according to some rules in a binary tree. The rule is that for all nodes, the right node is larger than the left node. Take a look at the picture below.


![Binarysearch](/images/binarysearch.gif)

21 is the root node, and next time 28 is inserted into the tree, the value is greater than 21, so it goes to the right. The next value, 14, is less than 21, so it goes to the left. And the figure below is an animation of finding a value in a binary search tree. The binary search tree has an average time complexity of O(logN), and in the worst case the tree is skewed to one side, it has a time complexity of O(N).

![Binarysearch2](/images/binarysearch2.gif)


##### Implement

```py
# Create Node and insert
class Node:
    def __init__(self,data):
        self.left = None
        self.right = None
        self.data = data
        
class BinarySearchTree(Node):
    def insert(self, data):
        self.root = self._insert_value(self.root, data)
        return self.root is not None

    def _insert_value(self, node, data):
        if node is None:
            node = Node(data)
        else:
            if data <= node.data:
                node.left = self._insert_value(node.left, data)
            else:
                node.right = self._insert_value(node.right, data)
        return node

# Search node
    def find(self, key):
        return self._find_value(self.root, key)

    def _find_value(self, root, key):
        if root is None or root.data == key:
            return root is not None
        elif key < root.data:
            return self._find_value(root.left, key)
        else:
            return self._find_value(root.right, key)

        def delete(self, key):
        self.root, deleted = self._delete_value(self.root, key)
        return deleted

    def _delete_value(self, node, key):
        if node is None:
            return node, False

        deleted = False
        # If node is delete node
        if key == node.data:
            deleted = True
            # If deleting node has 2 children
            if node.left and node.right:
                # Find and replace the leftmost node in the right subtree
                parent, child = node, node.right
                while child.left is not None:
                    parent, child = child, child.left
                child.left = node.left
                if parent != node:
                    parent.left = child.right
                    child.right = node.right
                node = child
            # If there is only one child node, replace it with that node
            elif node.left or node.right:
                node = node.left or node.right
            # If there are no child nodes, just delete
            else:
                node = None
        elif key < node.data:
            node.left, deleted = self._delete_value(node.left, key)
        else:
            node.right, deleted = self._delete_value(node.right, key)
        return node, deleted

```

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)

#### Tree traversal algorithm

It is used when you want to check and check all the nodes in the tree. Traversal algorithms include `pre-order traversal`, `post-order traversal`, `in-order traversal`, and `level-order traversal`. Of these, sorted data in a binary tree can be obtained through `in-order traversal`.


![Pre-order traversal](/images/preorder.gif)

Pre-order traversal goes in the order of root node -> left subtree -> right subtree.

```py
def pre_order_traversal(self):
        def _pre_order_traversal(root):
            if root is None:
                pass
            else:
                print(root.data)
                _pre_order_traversal(root.left)
                _pre_order_traversal(root.right)
        _pre_order_traversal(self.root)
```

![Post-order traversal](/images/postorder.gif)

Post-order traversal goes in the order of left subtree -> root node -> right subtree.

```py
def post_order_traversal(self):
        def _post_order_traversal(root):
            if root is None:
                pass
            else:
                _post_order_traversal(root.left)
                _post_order_traversal(root.right)
                print(root.data)
        _post_order_traversal(self.root)
```

![In-order traversal](/images/inorder.gif)

In-order traversal is traversed in the order of left subtree -> root node -> right subtree.

```py
  def in_order_traversal(self):
        def _in_order_traversal(root):
            if root is None:
                pass
            else:
                _in_order_traversal(root.left)
                print(root.data)
                _in_order_traversal(root.right)
        _in_order_traversal(self.root)
```
![Level-order traversal](/images/levelorder.gif)

Level-order traversal is implemented in a width-first traversal method.

```py
 def level_order_traversal(self):
        def _level_order_traversal(root):
            queue = [root]
            while queue:
                root = queue.pop(0)
                if root is not None:
                    print(root.data)
                    if root.left:
                        queue.append(root.left)
                    if root.right:
                        queue.append(root.right)
        _level_order_traversal(self.root)
```

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)

#### Heap

A complete binary tree in which the key value of each node is not smaller or larger than the key value of the child node of the corresponding node.<br>

- Key value relationship is established only between parent-child nodes and does not affect sibling nodes.
- The maximum number of child nodes depends on the type of heap, but up to 2 in a binary tree (assuming a complete binary tree is used).
- The i-th node has 2 child nodes, the left child node is 2i, the right child node is 2i+1, and the parent node is i/2.

* Max heap
: Heap where the key value of each node is not smaller than the key value of its child node

```py
key(T.parent(v)) > key(v)
```

* Min heap
: Heap where the key value of each node is not greater than the key value of its child node

```py
key(T.parent(v)) < key(v)
```

* Time complexity
: O(log n)


* Insertion
- Add the value you want to insert to the last element of the tree.
- The exchange of seats is repeated until they are satisfied while comparing the relationship with the parent node.

* Deletion
- Since only the root node can be deleted from the heap, remove the root node.
- Move the last node to the root.
- Compared with the child node, it moves until the condition is satisfied.
heapq module
: The heap queue module provided by Python, allowing you to treat general lists like min heap


##### Implement

```py
import heapq

# add node : use heappush method

heap = [] 
heapq.heappush(heap, 1)

# delete node : use heappop method
# Take out the smallest element and return, automatically the next smallest element becomes the root note

return heapq.heappop(heap)

# Accessing the index to just return without fetching the minimum value

print(heap[0])

# Note: There is no guarantee that index 1 is the 2nd smallest, so if you want to get the nth smallest element, you have to subtract n-1 elements.

# Converting previously used list to heap: use heapify method


tmp = [7, 5, 8, 3]
heapq.heapify(tmp)


# Making the largest heap: using tuples containing priorities

import heapq

nums = [4, 1, 7, 3, 8, 5]
heap = []

for num in nums:
  heapq.heappush(heap, (-num, num))  # (priority, value)

while heap:
  print(heapq.heappop(heap)[1])  # index 1
```

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)



#### Priority queue

The priority queue is a data structure in which data with the highest priority can be retrieved first. It is not difficult to implement directly using arrays, but Python provides a built-in module called heapq, so if you do not need additional operations, it is better to use the built-in module.

1. Creation of priority queues and element insertion

You can easily create a priority queue or heap using heapq.heappush. The first argument is a list, which is the heap itself, and the second argument is a tuple. The first element of the tuple is the priority value, and the second element is the data. If a general value other than a tuple is entered as the second argument of the function, a heap is created based on the value. Note that the heap provided by Python is a min-heap. The time complexity per insertion is O(log n).

```py
import heapq
h = []
heapq.heappush(h, (3, "Go to home"))
heapq.heappush(h, (10, "Do not study"))
heapq.heappush(h, (1, "Enjoy!"))
heapq.heappush(h, (4, "Eat!"))
heapq.heappush(h, (7, "Pray!"))
print(h)

# The result shows the heap implemented as an array
[(1, 'Enjoy!'), (4, 'Eat!'), (3, 'Go to home'), (10, 'Do not study'), (7, 'Pray!')]
```

2. Take out elements
Element extraction can be implemented with heapq.heappop. The time complexity for each pull is O(log n).

```py
import heapq
h = []
heapq.heappush(h, (3, "Go to home"))
heapq.heappush(h, (10, "Do not study"))
heapq.heappush(h, (1, "Enjoy!"))
heapq.heappush(h, (4, "Eat!"))
heapq.heappush(h, (7, "Pray!"))
first = heapq.heappop(h)
second = heapq.heappop(h)
third = heapq.heappop(h)
print("first:", first)
print("second:", second)
print("third:", third)

# result
first: (1, 'Enjoy!')
second: (3, 'Go to home')
third: (4, 'Eat!')
```

3. Creating a heap sort from an array

If the array is made into a heap using method 1, the time complexity is O(n log n). However, the time complexity of the optimal algorithm for building a heap from an array is known as O(n). Python provides a heapq.heapfy function that can make an array heap in O(n) time. Note that the array itself turns into a heap.

```py
import heapq
h = [(3, "Go to home"), (10, "Do not study"), (1, "Enjoy!"), (4, "Eat!"), (7, "Pray!")]
heapq.heapify(h)
print(h)

# result
[(1, 'Enjoy!'), (4, 'Eat!'), (3, 'Go to home'), (10, 'Do not study'), (7, 'Pray!')]
```

4. Max-heap

heapq basically only supports Min-heap. Is there any way to use the maximum heap? There is a way to do it using heapq._heapfy_max or heapq._heappop_max, but it is a half function because push is not supported. The only way is to convert the key value and put it in. The time required to change the key of all elements is O(n), and the time complexity of obtaining all the heap elements is O(n log n), so even if you change keys while rotating all elements, it does not matter to the total time complexity. In the previous example, the key value is an integer, so you can add -.

```py
import heapq
h = [(3, "Go to home"), (10, "Do not study"), (1, "Enjoy!"), (4, "Eat!"), (7, "Pray!")]
max_h = [(-ele[0], ele[1]) for ele in h]
heapq.heapify(max_h)
print(max_h)
```

However, this method has the hassle of having to change the data each time when using push individually. To avoid this hassle, you have to define a class that wraps the functions of the heapq module and creates a max heap. By using the __lt__ built-in method, the comparison can be reversed, so it is not difficult to implement.
> Note : that both of the above methods must provide a way to keep the original data. To do this, we need to implement the wrapping and unwrapping of the data.
The following code is a simple implementation of the max_heapq module using the __lt__ built-in method. Note that when pushing or popping an element, it wraps and unwraps the element.

```py
import heapq

class ReverseLessThan(object):
    def __init__(self, value):
        self.value = value

    def __lt__(self, other):
        return self.value > other.value

    def __repr__(self):
        return str(self.value)


def heappush(heap, item):
    reverse_item = ReverseLessThan(item)
    heapq.heappush(heap, reverse_item)


def heappop(heap):
    reverse_item = heapq.heappop(heap)
    return reverse_item.value


def heapify(lst):
    for i, ele in enumerate(lst):
        lst[i] = ReverseLessThan(ele)
    heapq.heapify(lst)


if __name__ == "__main__":
    h = []
    heappush(h, (3, "Go to home"))
    heappush(h, (10, "Do not study"))
    heappush(h, (1, "Enjoy!"))
    heappush(h, (4, "Eat!"))
    heappush(h, (7, "Pray!"))
    heappush(h, (4, "Dup Eat!"))

    print(h)

    count = 1
    while h:
        print("%dth : %s" % (count, heappop(h)))
        count += 1

    lst = ["ab", "dh", "hihi", "kk1", "power"]
    heapify(lst)
    print(lst)
    count = 1
    while lst:
        print("%dth : %s" % (count, heappop(lst)))
        count += 1
```

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)







### Graph

- What is a graph?

A graph is a data structure made up of vertices and edges. It can be viewed as an organization chart that expresses the relationship between vertices. In that sense, a tree is a kind of graph. However, unlike trees, graphs may or may not have edges per vertex, and the concept of root node, parent and child does not exist. In addition, graphs can be understood in a flexible way to represent network models, that is, objects and their relationships to them. Various examples can be expressed in graphs in real life. Representatively, there are subway maps and urban roads. Since there are many methods that can be used in this way, various questions can be made. Graphs are used a lot in algorithms. In particular, you should be familiar with `DFS` and `BFS`, which are ways of traversing graphs.

- Graph term

![Graph](/images/graph.png)

- Vertice : Also known as nodes, vertices store data. (0, 1, 2, 3)
- Edge : Also known as links (arcs), they represent the relationship between nodes.
- Adjacent vertex : Vertices connected by edges from above `vertex 0 and vertex 1 are adjacent vertices`
- Simple-path : No repeated vertices in the path, paths that do not cut the same edge
- Degree : The number of vertices adjacent to one vertex in an undirected graph (the degree of vertex 0 is 3)
- Out-degree : A term used in direction graphs, which refers to the number of edges going out from a node.
- In-degree : This term is used in direction graphs and refers to the number of edges coming from an external node.

- How to implement the graph

 
There are two ways to implement a graph: `Adjacency Materix` and `Adjacency List`. The two implementations each have opposite pros and cons, and most of them use the `Adjacency list` format a lot.




#### Direction graph

![Direction_graph](/images/direction_graph.png)

A direction graph is a graph in which a direction exists on an edge connecting two vertices. You can only move in the direction of the edge.



#### Non-Direction graph

![Non-Direction_graph](/images/non_direction_graph.png)

An undirected graph is a graph with no direction on the edges connecting two vertices.



#### Adjacency matrix

![Adjacency_matrix](/images/adjacency_matrix.png)

Adjacency matrix is a two-dimensional array of nodes in a graph. In the shape of the completed array, 1, 2, 3, 4, 5, 6 is inserted into the node connecting the vertices, and 1 if other nodes are adjacent vertices, or 0 otherwise.

- Advantages
  1. Since the edge information of all vertices is contained in a two-dimensional array, checking the position of the array is possible with a time complexity of O(1) when retrieving connection information for two points.
  2. It is relatively simple to implement.

- Disadvantages
  1. It takes O(n²) time complexity since it is necessary to substitute edge information for all vertices.
  2. Since a two-dimensional array is unconditionally required, more space than necessary is wasted.

#### Adjacency list

![Adjacency_list](/images/adjacency_list.png)

An adjacency list is a list of nodes in a graph. It is mainly implemented by creating a list array of vertices and establishing the relationship.

- Advantages
  1. When searching for connection information of vertices, it is possible in O(n) time. (n: number of edges)
  2. Less space is wasted because it only uses as much space as needed.

 

- Disadvantages
  1. It takes longer to check whether two specific points are connected compared to adjacent matrices. (Search speed slower than array)
  2. It is relatively difficult to implement.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)

#### Graph traversal

Starting at a random vertex in the graph and visiting all vertices once

- Search vs Traversal

  - Search : How to quickly find the data you want by index or hashing
  - Traversal : How to visit all nodes using a specific traversal algorithm

  - The target of search is a specific value (node) in the graph. The purpose of the search is a sword that quickly finds the object of interest.

  - On the other hand, in traversal, not only specific nodes but all nodes are of interest. In other words, the graph itself is the object of interest in the circuit. It is also possible to find a specific value through traversal and it becomes possible to manipulate the graph.

- Why is graph traversing important?

  - Since graph search visits all vertices, the characteristics of the graph can be known through the search.
  - Also, you can process graphs because you can check and update while visiting. A spanning tree can be obtained by using a graph search technique such as BFS and DFS.
  - In other words, it can be created as (Graph -> Spanning Tree or MST-Minimu Spanning Tree) through search.

##### Depth-first search(DFS)

- A search technique that preferentially searches for child nodes

- Priority search for adjacent nodes (child nodes) that have not yet been visited

- Depth-first search is a form of digging in only one direction and then returning and digging the other side when there is no more place to sell.

- Depth-first search is implemented through Stack.

- Therefore, when implementing DFS, you can use stack or recursive functions.

- If you use a recursive function, you have to be careful of stack overflow because it uses the call stack.

- Used for Spanning Tree, Connected Component, Strongly Connected Component, etc.

```py
# Example Code

def dfs(graph, start_node):
    visit = list()
    stack = list()
    stack.append(start_node)
    while stack:
        node = stack.pop()
        if node not in visit:
            visit.append(node)
            stack.extend(graph[node])
    return visit

```

##### Breadth-first search(BFS)

-A search technique to search for sibling nodes first. (Also called level-order traversal)

-Priority search for neighboring nodes (sibling nodes of the current node) of previous nodes (parent nodes) that have not yet been visited

-If BFS is used, BFS is used for shortest path search instead of DFS because it is possible to expand to the node with the best heuristic value by finding the heuristic value at each search.

-Usually, breadth-first search is implemented through a queue.

-Use for shortest path search, Spanning Tree, Connected Component, Strongly Connected Component, etc.

```py

# Example Code

from queue import Queue

def bfs(graph, start_node):
    visit = set()
    q = Queue()

    q.put(start_node)

    while q.qsize() > 0:
        node = q.get()
        if node not in visit:
            visit.add(node)
            for nextNode in graph[node]:
                q.put(nextNode)
    return visit

```


[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)



## Search algorithm

- Linear search

  * Algorithm to search sequentially by scanning from the front until an element with a desired key value is found in an array arranged in a straight line
  * If the number of elements in the array is n, the number of times to judge the condition is on average n/2 times.
  * The only way to use when searching in an unordered array of values

```
Example

i = 0
while True:
    if i == len(a):
        return -1
    if a[i] == key:
        return i
    i += 1
```

- Sentinel method: Linear search checks two termination conditions every iteration, so this is a method to reduce this cost in half.
- After adding the key value to be searched to the end of the array, if the found value is the same as the length of the array, failure is returned.

```
Example

a.append(key)
i = 0

while True:
    if a[i] == key:
        break
    i += 1
return -1 if i == len(a) else i
```

</br>

- Binary search
 
  * To use, the data in the array must be sorted
  * Faster search than linear search and efficient search in ascending or descending order
  * The search range is reduced by half by comparing the value to be found and the intermediate point value of the search range.

```
Example

def bin_search(a: Sequence, key: Any) -> int:

    pl = 0          # first index
    pr = len(a) -1  # last index

    while True:
        pc = (pl + pr // 2) # center index
        if a[pc] == key:
            return pc
        elif a[pc] < key:
            pl = pc + 1
        else:
            pr = pc -1
        if pl > pr:
            break
        return -1
```

- Hashing

  * Data can be added and deleted efficiently while searching.
  * How to find the location (index) to save the data with a simple operation
  * Access data based on the remainder (hash value) of each array key (element value) divided by the number of elements in the array
  * Elements created from the hash table are called buckets.

```
Example

a = [5, 6, 14, 20, 29, 34, 37, 51, 69, 75, -, -, -]

Index number of each element in the hash table divided by the number of elements by 13 = 5, 6, 1, 7, 3, 8, 11, 12, 4, 10

hash_table_a = [-, 14, -, 29, 69, 5, 6, 20, 34, -, 75, 37, 51]

# Add new element 35 : 35 % 13 = Add an element to index 9 (no need to move the element)

```

- In the hash method, if there is already data in the storage area, it can be replaced in two ways
  1. Chaining(Open hashing) : Manage elements with the same hash value as a linked list
  2. Open addressing : When a hash collision occurs, rerun the hash to find an empty bucket

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)



## Greedy Algorithm

- The greedy algorithm is a way to choose the best method eachtime in current situation
- In general situations, the greedy algorithm is often unable to guarantee an optimal solution. Therefore, it is necessary to review whether the optimal solution can be obtained simply by repeatedly selecting the best method.

### Example 1

Give change

You are a clerk in department store. You have to give back 1260coin as change to the customer. What is the minimum number of coins that can be traced back?

- Give back as far as possible from the largest unit.
- However, if the large unit is not a multiple of the small unit, review is necessary.

```
n = 1260
count = 0

array = [500, 100, 50, 10]

for coin in array:
    count += n // coin
    n %= coin

print(count)
```

### Example 2

One of the following two processes is repeatedly selected and performed until a certain number N becomes 1. However, the second operation can be selected only when N is divided by K.

1. N - 1
2. N / K

Find the minimum number of times one or two steps must be performed until N equals 1

> Condition: int(1 <= n <= 100000), int(2 <= K M= 100000)

-Since K is more than 2, division can reduce the number faster
-Divide as much as possible for N

```

n, k = map(int, input().split())

count = 0

while n > 1:
    if n % k == 0:
        n = n // k
        count += 1
    else:
        n -= 1
        count += 1

count += 1
print(count)

<!-- But like this loop too many times -->
```

```
<!-- refactoring -->

n, k = map(int, input().split())

count = 0

while True:
    <!-- Subtraction is performed at once until n is divided by k. -->
    target = (n // k) * k
    count += (n - target)
    n = target

    <!-- Escape the loop when it can no longer be divided -->
    if n < k:
        break

    <!-- devide by k -->
    count += 1
    n //= k

<!-- Subtract 1 from the last remaining number -->
count += (n - 1)
print(count)
```

### Example 3

Given a string S consisting of only numbers (0 to 9) each digit. Check all numbers one by one from left to right, and puts the'\*' or'+' operator between the numbers to create the largest number that can be made. However, it is assumed that all operations are performed in order from left to right.
Create a program that fits the above conditions

> For example, the largest number that can be made with the string 02984 is ((((0 + 2) _ 9) _ 8) \* 4) = 576. Also, the input value is given so that the largest number that can be made is always an integer less than 2 billion.

```
s = input()

<!-- convert first list value string to integer -->
result = int(s[0])

for i in range(1, len(s)):

<!-- if one of them or both <= 1, choose '+' -->
    num = int(s[i])
    if result <= 1 or num <= 1:
        result += num
    else:
        result *= num

print(result)

```

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)





## Recursive algorithm

- Calling the function itself inside the function
- It is easy to fall into an infinite loop, so you must specify the termination condition.
- All iterations can be expressed as recursive functions

```
def f(n):
    if n > 1:
        return n * f(n-1)
    else:
        return 1

print(f(5))   >>> 120
```

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)



