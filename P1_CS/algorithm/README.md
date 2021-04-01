# Algorithm

- [Tips for Coding Interview](#Tips-for-Coding-Interview)
- [Interview Questions for Algorithms](#Interview-Questions-for-Algorithms)
- [Coding Exercises](#Coding-Exercises)
- [Strategic Approach to Problem Solving](#Strategic-Approach-to-Problem-Solving)
- [Theory](#Theory)
  - [Array](#Array)
  - [Stack](#Stack)
  - [Queue](#Queue)
  - [Hash Table](#Hash-Table)
  - [Sort](#Sort)
    - 선택정렬
    - 삽입정렬
    - 힙정렬
    - 퀵정렬
    - 병합정렬
  - [Tree](#Tree)
    - BST (이진탐색트리)
    - 힙
    - 우선순위 큐
    - 이진힙
  - [Graph](#Graph)
    - 방향그래프
    - 무방향그래프
    - 인접행렬
    - 인접리스트
    - 그래프순회
      - 너비우선탐색(DFS)
      - 깊이우선탐색(BFS)
  
  - [검색 알고리즘](#)
  - [Greedy Algorithm](#Greedy-Algorithm)
  - [Sorting Algorithm](#sorting-algorithm)
  - 최단거리알고리즘
  - 백트래킹
  - DP
  - 분할정복



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


선택 정렬은 알고리즘에 대해 배워본 적이 없는 사람도 쉽게 생각해낼 수 있는 정렬 알고리즘입니다. 왜냐하면 우리가 일상에서 무언가를 크기 순으로 나열할 때 흔히 사용되는 사고 방식이기 때문입니다.
선택 정렬은 정렬된 값을 배열의 맨 앞부터 하나씩 채워나가게 됩니다. 따라서, 뒤에 있는 index로 갈수록 비교 범위가 하나씩 점점 줄어드는 특성을 가지고 있습니다. (index 0에서는 0부터 n-1까지 비교해야 되지만, index n-1에서는 남은 숫자가 하나 밖어서 비교가 필요 없음)
입력 배열이 이미 정렬되어 있건 말건 관계없이 동일한 연산량을 가지고 있기 때문에 최적화 여자가 적어서 다른 O(N^2) 대비해도 성능이 떨어지는 편입니다.
이러한 성능 상의 한계 때문에 실전에서는 거의 보기 힘들지만, 가장 구현이 쉬운 정렬 알고리즘이라서, 알고리즘 수업 시간에는 한 번씩 꼭 접하게 되는 유명한 정렬 알고리즘입니다.


`170cm, 180cm, 150cm, 160cm`

예를 들어, 위와 같이 키를 알고 있는 네 친구들을 키 순으로 세우려면, 우선 4명의 키를 모두 비교하여 키가 제일 작은 150cm인 친구를 맨 앞에 세웁니다.

키가 150cm인 친구는 맨 앞에 세웠으니, 이제 나머지 세 친구의 키를 비교하여 키가 제일 작은 160cm인 친구를 그 다음에 세웁니다. 이제는 키가 170cm인 친구와 180cm인 친구 둘만 남았습니다. 둘 중에 170cm 친구가 더 작기 때문에 이 친구를 먼저 세우고, 그 다음 180cm인 친구를 마지막에 세웁니다.



Index | Value 
------------ | ------------- 
0 | 모든 값 중 가장 작은 값
1 | 첫번째 값(Index=0)을 제외하고 남은 값 중에서 가장 작은 값
... | ...
i | i번째 부터 n-1 번째까지 값 중 가장 작은 값
n-2	| n-2번째와 n-1 번째까지 값 중 가장 작은 값
n-1	| 마지막에 남은 하나의 값 (비교 대상 없음)

	
즉, 크기 n의 배열이 주어졌을 때, index 0부터 n-1까지의 모든 index i에 대해서, i번째 부터 n-1 번째까지 값 중 가장 작은 값을 구해서 index i에 놓으면 정렬된 배열을 얻을 수가 있습니다. 모든 index에 대해서 그 index에 위치시킬 값을 “선택”하기 때문에 이 정렬 알고리즘을 “선택 정렬”또는 “Selection Sort”이라고 부릅니다.


##### 구현

두 개의 반복문이 필요합니다. 내부 반복문에서는 현재 index부터 마지막 index까지 최소값의 index를 찾아내고, 외부 반복문에서는 이 최소값의 index와 현재 index에 있는 값을 상호 교대(swap)합니다. 외부 반복문에서는 index i를 0에서 n-2(또는 n-1. 마지막 index에서는 남는 값이 하나 밖에 없기 때문에 대세에 지장 없음)까지 진행시키며, 내부 반복문에서 이미 정렬된 값들에서는 관심이 없기 때문에 index j를 i에서 n-1까지 진행시킵니다. 각 index에 대해서 최소값을 찾기 위해 대소 비교는 여러번 일어나나 상호 교대(swap)은 딱 한번만 알어납니다.



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

##### 복잡도 

1. 선택 정렬은 별도의 추가 공간을 사용하지 않고 주어진 배열이 차지하고 있는 공간 내에서 값들의 위치만 바꾸기 때문에 O(1)의 공간 복잡도를 가집니다.
2. 시간 복잡도는 우선 루프문을 통해 모든 인덱스에 접근해야 하기 때문에 기본적으로 O(N)을 시간을 소모하며, 하나의 루프에서는 현재 인덱스의 값과 다른 인덱스의 값들과 비교하여 최소값을 찾은 후 현재 인덱스에 있는 값과 상호 자리 교대를(swap)해야 해야하기 때문에 O(N)을 시간이 필요하게 됩니다. 따라서 선택 정렬은 총 O(N^2)의 시간 복잡도를 가지는 정렬 알고리즘입니다.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)

#### 삽입정렬


[Insert sort Explain-Video](https://youtu.be/ROalU379l3U)


삽입 정렬은 한마디로 표현하면 정렬 범위를 1칸씩 확장해나가면서 새롭게 정렬 범위에 들어온 값을 기존 값들과 비교하여 알맞은 자리에 꼽아주는 알고리즘입니다.
선택/거품 정렬은 패스가 거듭될 수록 탐색 범위가 줄어드는 반면에 삽입 정렬은 오히려 점점 정렬 범위가 넚어집니다.
큰 크림에서 보았을 때 바깥 쪽 루프는 순방향, 안 쪽 루프는 역방향으로 진행하고 있습니다.


예를 들어, 다음과 같이 1부터 5까지 총 5개의 숫자가 들어있는 배열에 있다고 가정해보겠습니다.

```
[2, 1, 5, 4, 3]
```

맨 처음에는 첫번째 2개의 값만 정렬 범위에 포함시키고 생각해보겠습니다. 앞에 있는 값 2는 뒤에 있는 값 1보다 작기 때문에 서로 자리를 바꿔줍니다.

```
[2, 1]: 2 > 1 => swap
 ^  ^
[1, 2]
 *  *
```

그 다음에는 기존의 정렬 범위에 한칸 확장하여 세번째 값을 추가시키고 생각해보겠습니다. 기존 정렬 범위에서 가장 큰 값인 2와 새롭게 추가된 5를 비교하면 자리를 바꿀 필요가 없다는 것을 알 수 있습니다. 기존에 정렬 범위에 있던 두 개의 값은 이 전 패스에서 이미 정렬이 되어 있기 때문에 굳이 1과 5를 비교할 필요는 없습니다.

```
[1, 2, 5]: 2 < 5 => OK
    ^  ^
[1, 2, 5]
 *  *  *
```

다음 패스에서는 정렬 범위를 한 칸 더 확장하여 4번째 값을 추가시키고 생각해볼 차례입니다. 기존 정렬 범위에서 가장 큰 값인 5와 새롭게 추가된 4를 비교하면, 앞에 있는 값이 뒤에 있는 값보다 크기 때문에 서로 자리를 바꿔야 합니다. 이제 기존 정렬 범위에서 두 번째로 큰 값인 2와 방금 자리를 교체 당한 4를 비교해보면 더 이상 자리를 바꿀 필요가 없다는 것을 알 수 있습니다.

```
[1, 2, 5, 4]: 5 > 4 => swap
       ^  ^
[1, 2, 4, 5]: 2 < 4 => OK
    ^  ^
[1, 2, 4, 5]
 *  *  *  *
```

마지막 패스에서는 정렬 범위를 전체로 확장하여 마지막 값까지 포함시킵니다. 여태까지 했던 방식과 동일하게 새로 추가된 값과 기존에 있던 값들을 뒤에서 부터 비교해나가면 2번의 자리 교체가 필요하다는 것을 알 수 있습니다.

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

##### 구현

1. 두 개의 반복문이 필요합니다. 내부 반복문에서는 정렬 범위에 새롭게 추가된 값과 기존 값들을 뒤에서 부터 계속해서 비교해나가면서 앞의 값이 뒤의 값보다 클 경우 자리 교대(swap)를 합니다. 외부 반복문에서는 정렬 범위를 2에서 N으로 확대해 나갑니다.

```py
def insertion_sort(arr):
    for end in range(1, len(arr)):
        for i in range(end, 0, -1):
            if arr[i - 1] > arr[i]:
                arr[i - 1], arr[i] = arr[i], arr[i - 1]
```

2. 기존에 있던 값들은 이전 패스에서 모두 정렬되었다는 점을 활용하면 불필요한 비교 작업을 제거할 수 있습니다. 예를 들면, 아래와 같이 기존 정렬 범위 [1, 2, 3, 5]에 4가 새롭게 추가된다면, 5는 4보다 크기 때문에 swap이 필요하지만, 3은 4보다 작기 때문에 swap이 필요없습니다. 그리고 3보다 앞에 있는 숫자들은 기존 패스에서 이미 정렬을 해놓았기 때문에 당연히 3보다는 작을 것이며, 더 이상의 4와 대소 비교는 무의미합니다. 이 사실을 이용하면, 새롭게 추가된 값보다 작은 숫자를 만나는 최초의 순간까지만 내부 반복문을 수행해도 됩니다.

이 최적화를 적용하면, 정렬된 배열이 들어올 경우, O(N)의 시간 복잡도를 달성할 수 있습니다. 예를 들어, 다음과 같이 5개의 숫자가 된 배열이 들어오면 각 패스 당 단 한 번 총 4번의 비교만으로 해당 배열이 완전히 정렬되었음을 알아내고 삽입 정렬을 완료할 수 있습니다.


```py
def insertion_sort(arr):
    for end in range(1, len(arr)):
        i = end
        while i > 0 and arr[i - 1] > arr[i]:
            arr[i - 1], arr[i] = arr[i], arr[i - 1]
            i -= 1
```



3. swap 작업없이 단순히 값들을 shift 시키는 것만으로도 삽입 정렬의 구현이 가능합니다. 앞의 값이 정렬 범위에 추가시킨 값보다 클 경우 앞의 값을 뒤로 밀다가 최초로 작은 값을 만나는 순간 그 뒤에 추가된 값을 꼽으면 됩니다.

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


##### 복잡도

1. 삽입 정렬은 별도의 추가 공간을 사용하지 않고 주어진 배열이 차지하고 있는 공간 내에서 값들의 위치만 바꾸기 때문에 O(1)의 공간 복잡도를 가집니다.
2. 시간 복잡도는 우선 루프문을 통해 정렬 범위를 2개로 시작해서 전체로 확장해야 하기 때문에 기본적으로 O(N)을 시간을 소모하며, 각 패스에서는 정렬 범위에 새롭게 추가된 값과 기존 값들의 대소 비교 및 자리 교대를 위해서 O(N)을 시간이 필요하게 됩니다. 따라서 삽입 정렬은 총 O(N^2)의 시간 복잡도를 가지는 정렬 알고리즘입니다.
3. 아래에서 다룰 최적화를 통해서 부분적으로 정렬된 배열에 대해서 성능을 대폭 개선할 수 있으며, 특히 완전히 정렬되어 있는 배열이 들어올 경우, O(N)까지도 시간 복잡도를 향상시킬 수 있습니다.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)


#### 버블정렬


[Bubble Sort Explain-Video](https://youtu.be/lyZQPjUT5B4)


거품 정렬은 큰 그림에서 보았을 때 뒤에서 부터 앞으로 정렬을 해나가는 구조를 가지고 있습니다. 즉, 맨 뒷자리에 제일 큰 값을 제일 뒤로 보내고, 제일 큰 값 바로 앞에 두번째로 큰 값을 보냅니다. 이를 위해 배열 내의 값들을 앞뒤로 서로 비교해서 자리를 바꾸는 작업을 지속적으로 수행해야 합니다. 이렇게 큰 값을 계속해서 뒤로 보내는 모습이 마치 방울이 이동하는 것과 같이 보여서 거품 정렬이라는 이름이 붙어졌습니다.


먼저 거품 정렬을 통해 어떻게 가장 큰 값을 맨 뒤로 보내는지에 대해서 알아보겠습니다. 맨 첫번째 값부터 시작해서 다음 값들과 차례로 비교하면서 앞의 값이 더 크면 뒤의 값과 자리를 바꾸면 됩니다.

다음과 같이 1부터 5까지 총 5개의 숫자가 들어있는 배열에 대해서 위 로직을 적용해보겠습니다.

```
[4, 3, 5, 1, 2]
```
먼저, 4과 3를 비교합니다. 4가 3보다 크기 때문에 자리를 바꿉니다.

```
[4, 3, 5, 1, 2]
 ^  ^
4 > 3 => Swap
[3, 4, 5, 1, 2]
```
그 다음과 4과 5를 비교합니다. 4가 5보다 작기 때문에 자리를 바꿀 필요가 없습니다.
```
[3, 4, 5, 1, 2]
    ^  ^
4 < 5 => No Swap
```
그 다음과 5과 1를 비교합니다. 5가 1보다 크기 때문에 자리를 바꿉니다.
```
[3, 4, 5, 1, 2]
       ^  ^
5 > 1 => Swap
[3, 4, 1, 5, 2]
```
그 다음과 5과 2를 비교합니다. 5가 2보다 크기 때문에 자리를 바꿉니다.

```
[3, 4, 1, 5, 2]
          ^  ^
5 > 2 => Swap
[3, 4, 1, 2, 5]
             *
```

이렇게 맨 처음 값부터 시작해서 계속해서 그 다음 값과 대소를 비교하여 앞의 값이 뒤의 값보다 클 경우 자리를 바꿔주면 결국 제일 큰 값을 맨 뒤로 보낼 수가 있습니다.

이 과정을 모든 값으로 확장하면 다음과 같이 두 번째로 큰 값을 제일 큰 값 바로 앞으로 보낼 수 있고, 세 번째로 큰 값을 두 번째로 큰 값 바로 앞으로 보낼 수 있습니다.


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



- 거품 정렬은 점점 큰 값들을 뒤에서 부터 앞으로 하나씩 쌓여 나가게 때문에 후반으로 갈수록 정렬 범위가 하나씩 줄어들게 됩니다.
- 왜냐하면, 다음 패스에서는 이전 패스에서 뒤로 보내놓은 가장 큰 값이 있는 위치 전까지만 비교해도 되기 때문입니다.
- 제일 작은 값을 찾아서 맨 앞에 위치시키는 선택 정렬과 비교했을 때 정반대의 정렬 방향을 가집니다.
- 다른 정렬 알고리즘에 비해서 자리 교대(swap)가 빈번하게 일어나는 경향을 가지고 있습니다. 예를 들어, 선택 정렬의 경우 각 패스에서 자리 교대가 딱 한번만 일어납니다.
- 최적화 여지가 많은 알고리즘입니다. 예를 들어, 위 그림에서 Pass 5는 생략할 수 있는 패스입니다. 왜냐하면 Pass 4에서 한 번도 자리 교대가 일어나지 않았기 때문입니다.



##### 구현 

선택 정렬과 마찬가지로 두 개의 반복문이 필요합니다. 내부 반복문에서는 첫번째 값부터 이전 패스에서 뒤로 보내놓은 값이 있는 위치 전까지 앞뒤 값을 계속해서 비교해나가면서 앞의 값이 뒤의 값보다 클 경우 자리 교대(swap)를 합니다. 외부 반복문에서는 뒤에서 부터 앞으로 정렬 범위를 n-1부터 1까지 줄여나갑니다.

```py
def bubble_sort(arr):
    for i in range(len(arr) - 1, 0, -1):
        for j in range(i):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
```


이전 패스에서 앞뒤 자리 비교(swap)이 한 번도 일어나지 않았다면 정렬되지 않는 값이 하나도 없었다고 간주할 수 있습니다. 따라서 이럴 경우, 이후 패스를 수행하지 않아도 됩니다.


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

이전 패스에서 앞뒤 자리 비교(swap)가 있었는지 여부를 체크하는 대신 마지막으로 앞뒤 자리 비교가 있었던 index를 기억해두면 다음 패스에서는 그 자리 전까지만 정렬해도 됩니다. 따라서 한 칸씩 정렬 범위를 줄여나가는 대신 한번에 여러 칸씩 정렬 범위를 줄여나갈 수 있습니다.

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


##### 복잡도

거품 정렬은 별도의 추가 공간을 사용하지 않고 주어진 배열이 차지하고 있는 공간 내에서 값들의 위치만 바꾸기 때문에 O(1)의 공간 복잡도를 가집니다.
시간 복잡도는 우선 루프문을 통해 맨 뒤부터 맨 앞까지 모든 인덱스에 접근해야 하기 때문에 기본적으로 O(N)을 시간을 소모하며, 하나의 루프에서는 인접한 값들의 대소 비교 및 자리 교대를 위해서 O(N)을 시간이 필요하게 됩니다. 따라서 거품 정렬은 총 O(N^2)의 시간 복잡도를 가지는 정렬 알고리즘입니다.
하지만, 거품 정렬은 부분적으로 정렬되어 있는 배열에 대해서는 최적화를 통해서 성능을 대폭 개선할 수 있으며, 완전히 정렬되어 있는 배열이 들어올 경우, O(N)까지도 시간 복잡도를 향상시킬 수 있습니다.


[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)


#### 병합정렬

[Merge sort Explain-Video](https://youtu.be/XaqR3G_NVoo)

병합 정렬은 분할 정복 (Devide and Conquer) 기법과 재귀 알고리즘을 이용해서 정렬 알고리즘입니다. 즉, 주어진 배열을 원소가 하나 밖에 남지 않을 때까지 계속 둘로 쪼갠 후에 다시 크기 순으로 재배열 하면서 원래 크기의 배열로 합칩니다.

예를 들어, 다음과 같이 1부터 8까지 총 8개의 숫자가 들어있는 배열에 있다고 가정해보겠습니다.
```
[6, 5, 3, 1, 8, 7, 2, 4]
```
먼저 하나의 배열을 두 개로 쪼갭니다.
```
[6, 5, 3, 1] [8, 7, 2, 4]
```
그리고 다시 두 개의 배열을 네 개로 쪼갭니다.
```
[6, 5] [3, 1] [8, 7] [2, 4]

```
마지막으로 디시 네 개의 배열을 여덜 개로 쪼갭니다.
```
[6] [5] [3] [1] [8] [7] [2] [4]
```
이제 더 이상 쪼갤 수가 없으니 두 개씩 합치기를 시작하겠습니다. 합칠 때는 작은 숫자가 앞에 큰 수자를 뒤에 위치시킵니다.
```
[5, 6] [1, 3] [7, 8] [2, 4]
```
이제 4개의 배열을 2개로 합칩니다. 각 배열 내에서 가장 작은 값 2개를 비교해서 더 작은 값을 먼저 선택하면 자연스럽게 크기 순으로 선택이 됩니다.
```
[1, 3, 5, 6] [2, 4, 7, 8]
```
최종적으로 2개의 배열도 마찬가지로 크기 순으로 선택하가면서 하나로 합치면 정렬된 배열을 얻을 수 있습니다.
```
[1, 2, 3, 4, 5, 6, 7, 8]
```


##### 구현

재귀를 이용해서 병합 정렬을 구현할 수 있습니다. 먼저 배열을 더 이상 나눌 수 없을 때 까지 (원소가 하나만 남을 때까지) 최대한 분할 후에, 다시 병합하면서 점점 큰 배열을 만들어 나가면 됩니다. 따라서 이 재귀 알고리즘의 기저 조건은 입력 배열의 크기가 2보다 작을 때이며, 이 조건에 해당할 때는 배열을 그대로 반환하면 됩니다.


파이선의 리스트 slice notation(arr[start:end])을 사용하면 다음과 같이 간결한 코드를 작성할 수 있습니다. 하지만, 리스트 slice를 할 때 배열의 복제가 일어나므로 메모리 사용 효율은 좋지 않습니다.
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
병합 결과를 담을 새로운 배열을 매번 생성해서 리턴하지 않고, 인덱스 접근을 이용해 입력 배열을 계속해서 업데이트하면 메모리 사용량을 대폭 줄일 수 있습니다. (In-place sort)

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

##### 복잡도


- 알고리즘을 큰 그림에서 보면 분할(split) 단계와 병합(merge) 단계로 나눌 수 있으며, 단순히 중간 인덱스를 찾아야 하는 분할 비용보다 모든 값들을 비교해야하는 병합 비용이 큽니다.
- 예제에서 보이는 것과 같이 8 -> 4 -> 2 -> 1 식으로 전반적인 반복의 수는 점점 절반으로 줄어들 기 때문에 O(logN) 시간이 필요하며, 각 패스에서 병합할 때 모든 값들을 비교해야 하므로 O(N) 시간이 소모됩니다. 따라서 총 시간 복잡도는 O(NlogN) 입니다.
- 두 개의 배열을 병합할 때 병합 결과를 담아 놓을 배열이 추가로 필요합니다. 따라서 공간 복잡도는 O(N) 입니다.
- 다른 정렬 알고리즘과 달리 인접한 값들 간에 상호 자리 교대(swap)이 일어나지 않습니다.



[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)



#### 힙정렬


[Heap sort Explain-Video](https://youtu.be/Xw2D9aJRBY4)


힙정렬을 알기 위해선 먼저 힙이 무엇인지 알아야 한다. 

여기서 힙은 힙트리로, 여러개의 값 들 중 가장 크거나 작은 값을 빠르게 찾기 위해 만든 이진 트리이다. 짧게 힙이라고 부른다.

![heapsort](/images/heapsort.gif) 

힙은 항상 완전 이진 트리의 형태를 띈다. 부모의 값은 항상 자식들의 값보다 크거나 (Max Heap) 작아야 (Min Heap) 한다는 규칙이 있다. 따라서 루트(뿌리) 노드에는 항상 데이터들 중 가장 큰 값 혹은 작은 값이 저장되어 있다.

힙 정렬의 방법은 아래와 같다.

1. 배열의 원소들을 전부 힙에 삽입
2. 가장 부모노드에 있는 값은 최댓값 혹은 최솟값이므로 루트를 출력하고 힙에서 제거
3. 힙이 빌 때 까지 2의 과정을 반복

힙정렬은 추가적인 메모리를 전혀 필요로하지 않는다는 점과 최악의 경우에도 항상 O(n log n) 의 성능을 발휘한다는 장점이 있다.


##### 구현

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



#### 퀵정렬

병합 정렬과 마찬가지로 퀵 정렬도 분할 정복 (Devide and Conquer) 기법과 재귀 알고리즘을 이용한 정렬 알고리즘입니다.

[Quick sort Explain-Video](https://youtu.be/ywWBy6J5gz8)


- 파이썬의 list.sort() 함수나 자바의 Arrays.sort()처럼 프로그래밍 언어 차원에서 기본적으로 지원되는 내장 정렬 함수는 대부분은 퀵 정렬을 기본으로 합니다.
- 일반적으로 원소의 개수가 적어질수록 나쁜 중간값이 선택될 확률이 높아지기 때문에, 원소의 개수에 따라 퀵 정렬에 다른 정렬을 혼합해서 쓰는 경우가 많습니다.
- 병합 정렬과 퀵 정렬은 분할 정복과 재귀 알고리즘을 사용한다는 측면에서는 유사해보이지만, 내부적으로 정렬을 하는 방식에서는 큰 차이가 있습니다.
- 병합 정렬은 항상 정 중앙을 기준으로 단순 분할 후 병합 시점에서 값의 비교 연산이 발생하는 반면, 퀵 정렬은 분할 시점부터 비교 연산이 일어나기 때문에 그 이후 병합에 들어가는 비용이 매우 적거나 구현 방법에 따라서 아예 병합을 하지 않을 수도 있습니다.

쉬운 이해를 위해서 다음과 같이 1부터 7까지 총 7개의 숫자가 들어있는 배열을 기준으로 설명하겠습니다.

```
[6, 5, 1, 4, 7, 2, 3]
```
항상 정 가운데를 기준으로 분할을 하는 병합 정렬과 달리, 퀵 정렬은 흔히 피봇(pivot)이라고 불리는 임의의 기준값을 사용합니다. pivot 값을 선택하는데는 여러가지 방법이 있지만 여기서는 간단한 설명을 위해 정 중앙에 위치한 4을 pivot으로 정하겠습니다. 그리고 다음과 같이 이 pivot 값을 기준으로 pivot보다 작은 값의 그룹과 pivot보다 큰 값의 그룹으로 나눕니다.

```
            p
[3, 2, 1] < 4 < [7, 5, 6]
```
위와 같이 pivot 값보다 작은 값들은 모두 왼편으로 몰고, 큰 값들은 모두 오른편으로 몰면 기준값은 정확히 정렬된 위치에 놓이게 됩니다. 또한 이런 방식으로 분할을 해놓으면 앞으로 더 이상 왼편에 있는 값들과 오른편에 있는 값들 간에는 비교를 할 필요가 없습니다. 따라서 반대편은 전혀 신경쓰지 않고 왼편이든 오른편이든 같은편 내의 값들 끼리만 비교 후 정렬을 할 수 있게 됩니다.

먼저 왼편을 동일한 방식으로 정렬해보도록 하겠습니다. 왼편의 정 가운데에 위치한 pivot 값인 2 보다 작은 값인 1인 왼쪽에 큰 값인 3은 오른쪽에 위치시켰습니다. 이제 양쪽 모두 값이 하나씩 밖에 없기 때문에 이로써 왼편의 정렬 작업은 완료되었습니다.
```
    p
[1] < 2 < [3]
```

오른편도 동일한 방식으로 정렬해보겠습니다. 오른편의 pivot 값인 5 보다 작은 값은 없으므로 7과 6을 모두 오른편에 위치시켰습니다.
```
    p
[] < 5 < [7, 6]
```

오른편의 오른편(?)에는 값이 2개가 있기 때문에 추가 정렬이 필요합니다. 왼편에는 값이 없지만 오른편에는 여전히 두 개의 값이 있기 때문에, 동일한 방식의 정렬을 적용하겠습니다.
```
      p
[6] < 7 < []
```
마지막으로 지금까지 좌우로 분할했던 값들을 모두 합치보면 다음과 같이 정렬된 배열을 얻을 수 있습니다.
```
[1, 2, 3, 4, 5, 6, 7]
```
지금까지 살펴본 것과 같이 퀵 정렬은 배열을 pivot 값 기준으로 더 작은 값과 큰 값으로 반복적으로 분할하여 정렬해나가는 방식을 취하고 있습니다.


##### 구현

위에 설명드린 기본 컨셉을 그대로를 코드로 구현할 수 있습니다. 먼저 리스트의 정 가운데 있는 값을 pivot 값으로 선택하고, pivot 값보다 작은 값, 동일한 값 그리고 큰 값을 담아둘 3개의 리스트를 생성합니다. 그리고 반복문을 통해 각 값을 pivot과 비교 후에 해당하는 리스트에 추가시킵니다. 그 다음 작은 값과 큰 값을 담고 있는 배열을 대상으로 퀵 정렬 함수를 재귀적으로 호출합니다. 마지막으로 재귀 호출의 결과를 다시 크기 순으로 합치면 정렬된 리스트를 얻을 수 있습니다.

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
위의 구현은 간결하고 이해하기 쉽지만 매번 재귀 호출될 때 마다 새로운 리스트를 생성하여 리턴하기 때문에 메모리 사용 측면에서 비효율적입니다. 큰 사이즈의 입력 데이터를 다뤄야하는 상용 코드에서는 이러한 단점은 치명적으로 작용할 수 있기 때문에 추가 메모리 사용이 적은 in-place 정렬이 선호됩니다.

> 처음부터 스스로 in-place 정렬을 구현하는 코드를 작성하기는 생각했던 것보다 쉽지 않을 수도 있습니다. 기존과 동일하게 값의 대소 비교를 위해서는 pivot 값을 사용하지만, 분할은 기준점은 pivot 값이 아닐 수도 있기 때문입니다. 왜냐하면, pivot 값을 기준으로 대소 비교를 했을 때 좌측과 우측에 여유 공간이 딱 맞는 경우가 드물기 때문입니다.

```py
# 메인 함수인 quick_sort()는 크게 sort()와 partition() 2개의 내부 함수로 나눠집니다. sort() 함수는 재귀 함수이며 정렬 범위를 시작 인덱스와 끝 인덱스로 인자로 받습니다. (둘다 inclusive) partition() 함수는 정렬 범위를 인자로 받으며 다음 로직을 따라서 좌우측의 값들을 정렬하고 분할 기준점의 인덱스를 리턴합니다. 이 분할 기준점(mid)는 sort()를 재귀적으로 호출할 때 우측 리스트의 시작 인덱스로 사용됩니다.

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


##### 복잡도

- 퀵 정렬의 성능은 어떻게 pivot 값을 선택 선택하느냐에 크게 달라질 수 있습니다. 이상적인 경우에는 pivot 값을 기준으로 동일한 개수의 작은 값들과 큰 값들이 분할되어 병합 정렬과 마찬가지로 O(NlogN)의 시간 복잡도를 가지게 됩니다.
- 하지만 pivot 값을 기준으로 분할했을 때 값들이 한 편으로 크게 치우치게 되면, 퀵 정렬은 성능은 저하되게 되며, 최악의 경우 한 편으로만 모든 값이 몰리게 되어 O(N^2)의 시간 복잡도를 보이게 됩니다.
- 따라서 상용 코드에서는 중앙값(median)에 가까운 pivot 값을 선택할 수 있는 섬세한 전략이 요구되며, 배열의 첫값과 중앙값 그리고 마지막값 중에 크기가 중간인 값을 사용하는 방법이 많이 사용됩니다.
- 퀵 정렬은 공간 복잡도는 구현 방법에 따라 달라질 수 있는데, 입력 배열이 차지하는 메모리만을 사용하는 in-place sorting 방식으로 구현을 사용할 경우, O(1)의 공간 복잡도를 가진 코드의 구현이 가능합니다.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)




### Tree

#### BST (이진탐색트리)

이진 탐색 트리에 들어가기에 앞서 먼저 이진 트리에 대해 간단하게 알아보자. 이진 트리란, 트리의 종류로 각 노드가 최대 2개의 자식 노드를 갖는 트리를 말한다. 즉, 이진 트리의 각 노드는 자식 노드를 갖고 있지 않을수도 있으며, 1개를 가질 수도, 2개를 가질 수도 있다.

이진 탐색 트리는 이진 트리에서 어떠한 규칙에 따라 나열한 트리이다. 이 규칙은 모든 노드에 대해서 왼쪽 노드보다 오른쪽 노드가 더 크게 나열하는 것이다. 아래 그림을 보자. 


![Binarysearch](/images/binarysearch.gif)

21이 루트 노드이고, 다음으로 28을 트리에 삽입을 할 때 21보다 큰 값이므로 오른쪽으로 간다. 그 다음 값인 14는 21보다 작으므로 왼쪽으로 간다. 그리고 아래 그림이 이진 탐색 트리에서 값을 찾는 것을 애니메이션으로 나타낸 것이다. 이진 탐색 트리는 평균 O(logN)의 시간복잡도를 가지며 트리가 한쪽으로만 치우친 최악의 경우 O(N)의 시간복잡도를 가진다. 

![Binarysearch2](/images/binarysearch2.gif)


##### 구현

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

#### 트리순회 알고리즘

트리에 있는 노드들을 다 살펴보고 확인하고 싶을 때 사용한다. 순회 알고리즘에는 전위 순회(pre-order traversal), 후위 순회(post-order traversal), 정위 순회(in-order traversal), 레벨 순회(level-order traversal) 등이 있다. 이 중 정위 순회를 통해 이진 트리에서 정렬된 데이터를 얻을 수 있다. 


![Pre-order traversal](/images/preorder.gif)

전위 순회는 뿌리 노드 -> 왼쪽 서브 트리 -> 오른쪽 서브 트리 순으로 순회한다.

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

후위 순회는 왼쪽 서브 트리 -> 뿌리 노드 -> 오른쪽 서브 트리 순으로 순회한다.

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

정위 순회는 왼쪽 서브 트리 -> 뿌리 노드 -> 오른쪽 서브 트리 순으로 순회한다.

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

레벨 순회는 너비 우선 순회방식으로 구현한다.

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

#### 힙

각 노드의 key값이 해당 노드의 자식노드의 key값보다 작지 않거나 크지 않은 완전 이진트리

- 키 값의 대소관계는 부모-자식 노드 사이 간에만 성립하며 형제 노드 사이에는 영향을 미치지 않음
- 자식노드의 최대 개수는 힙의 종류에 따라 다르지만 이진트리에서는 최대 2개 (완전이진트리를 사용한다고 가정하자.)
- i번째 노드의 자식노드가 2개인데 왼쪽 자식노드는 2i, 오른쪽 자식노드는 2i+1이고, 부모노드는 i/2가 된다.

* 최대 힙 (max heap)
: 각 노드의 키 값이 그 자식노드의 키 값보다 작지 않은 힙

```py
key(T.parent(v)) > key(v)
```

* 최소 힙 (min heap)
: 각 노드의 키 값이 그 자식노드의 키 값보다 크지 않은 힙

```py
key(T.parent(v)) < key(v)
```

* 시간복잡도
: O(log n)


* 삽입 연산 (insertion)
삽입하고자 하는 값을 트리의 가장 마지막 원소에 추가한다.
부모노드와의 대소관계를 비교하면서 만족할 때까지 자리 교환을 반복한다.

* 삭제 연산 (deletion)
힙에서는 루트 노드만 삭제가 가능하므로 루트 노드를 제거한다.
가장 마지막 노드를 루트로 이동시킨다.
자식노드와 비교하여 조건이 만족할 때까지 이동시킨다.
heapq module
: 파이썬에서 제공하는 힙큐 모듈, 일반적인 리스트를 min heap처럼 다룰 수 있게 해줌

##### 구현

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



#### 우선순위 큐

우선순위 큐는 우선 순위가 가장 높은 자료(data)를 가장 먼저 꺼낼 수 있는 자료 구조이다. 배열을 사용하면 직접 구현하기는 어렵지 않지만, 파이썬에서는 heapq라는 내장(built-in) 모듈로 제공이 되기 때문에, 추가적인 연산이 필요 없다면 내장 모듈을 사용하는게 좋다.

1. 우선 순위 큐의 생성 및 원소 삽입

heapq.heappush를 사용해 우선 순위 큐 또는 힙을 쉽게 생성할 수 있다. 첫번째 인자는 heap 자체인 list이고, 두번째 인자는 튜플인데 튜플의 첫번째 요소는 우선순위 값, 두번째 요소는 데이터를 넣어주면 된다. 함수의 두번째 인자로 튜플이 아닌 일반 값을 넣어주면, 값을 기준으로 heap을 만들어준다. 파이썬이 제공하는 힙은 최소힙(min-heap)이므로 주의하자. 삽입 별 시간 복잡도는 O(log n) 이다.

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

3. 배열로 부터 힙 정렬 만들기

1번의 방법으로 배열을 힙으로 만들면 시간 복잡도는 O(n log n)이다. 그러나 배열로 부터 힙을 만드는 최적의 알고리즘의 시간 복잡도는 O(n) 으로 알려져 있다. 파이썬에서는 O(n)의 시간으로 배열을 힙으로 만들 수 있는 heapq.heapfy 함수를 제공한다. 주의할 점은 배열 자체가 힙으로 바뀐다는 점이다.

```py
import heapq
h = [(3, "Go to home"), (10, "Do not study"), (1, "Enjoy!"), (4, "Eat!"), (7, "Pray!")]
heapq.heapify(h)
print(h)

# result
[(1, 'Enjoy!'), (4, 'Eat!'), (3, 'Go to home'), (10, 'Do not study'), (7, 'Pray!')]
```

4. 최대 힙 (max-heap)

heapq 는 기본적으로 최소 힙 밖에 지원을 안한다. 최대 힙을 쓸 수 있는 방법은 없을까?  heapq._heapfy_max 나 heapq._heappop_max 를 사용해서 하는 방법도 있지만, push를 지원해주지 않기 때문에, 반쪽짜리 기능이다. 유일한 방법은 키 값을 변환해서 넣는 수 밖에 없다. 모든 요소의 키를 바꾸는데 드는 시간은 O(n) 이고, 모든 힙 요소를 얻는데 드는 시간 복잡도는 O(n log n) 이므로, 요소를 모두 돌면서 키를 바꾼다 해도 전체 시간 복잡도에 문제가 되지 않는다. 앞의 예에서는 키 값이 정수 이므로 -를 붙여주면 된다.

```py
import heapq
h = [(3, "Go to home"), (10, "Do not study"), (1, "Enjoy!"), (4, "Eat!"), (7, "Pray!")]
max_h = [(-ele[0], ele[1]) for ele in h]
heapq.heapify(max_h)
print(max_h)
```

그러나 이 방법은 개별적으로 push를 사용할 때, 매번 데이터를 변경해 줘야 하는 번거로움이 있다. 이러한 번거로움을 피하고 싶으면, 결국 heapq 모듈의 기능을 래핑해 max 힙을 만드는 클래스를 정의하는 수 밖에 없다. __lt__ 내장 메소드를 활용하면, 비교는 반대로 할 수 있으므로, 어렵지 않게 구현할 수 있다.
주의할 점은 위 두가지 방법 다 원본 데이터를 유지할 수 있는 방법을 제공해 주어야 한다는 점이다. 이를 위해서 데이터의 래핑와 언래핑을 하도록 구현을 해야 한다.
다음 코드는 __lt__ 내장 메서드를 활용해 max_heapq 모듈을 간단히 구현해본 것이다. 요소를 push 하거나 pop 할때, 요소를 래핑하고 언래핑해 주고 있음에 유의하자.

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

- 그래프란 무엇인가?

그래프는 정점과 간선으로 이루어진 자료구조입니다. 정확히는 정점(Vertex)간의 관계를 표현하는 조직도라고 볼수도 있겠습니다. 그런면에서 트리는 그래프의 일종인 셈입니다. 다만 트리와는 달리 그래프는 정점마다 간선이 없을수도 있고 있을수도 있으며 루트 노드, 부모와 자식이라는 개념이 존재하지 않습니다. 또한 그래프는 네트워크 모델 즉, 객체와 이에 대한 관계를 나타내는 유연한 방식으로 이해할 수 있습니다. 실생활에서 다양한 예를 그래프로 표현할 수 있습니다. 대표적으로 지하철 노선도, 도심의 도로등이 있습니다. 이런식으로 활용할 수 있는 방법이 많기에 문제도 다양하게 출제를 할 수 있습니다. 그래프는 알고리즘에서 굉장히 많이 사용됩니다. 특히 그래프를 순회하는 방식인 DFS와 BFS를 잘 알아두어야 합니다. 

- 그래프 용어

![Graph](/images/graph.png)

- 정점(vertice) : 노드(node)라고도 하며 정점에는 데이터가 저장됩니다. (0, 1, 2, 3)
- 간선(edge): 링크(arcs)라고도 하며 노드간의 관계를 나타냅니다.
- 인접 정점(adjacent vertex) : 간선에 의해 연결된 정점으로 위에서 (정점0과 정점1은 인접 정점)
- 단순 경로(simple-path): 경로 중 반복되는 정점이 없는것, 같은 간선을 자나가지 않는 경로
- 차수(degree): 무방향 그래프에서 하나의 정점에 인접한 정점의 수 (정점 0의 차수는 3)
- 진출 차수(out-degree) : 방향그래프에서 사용되는 용어로 한 노드에서 외부로 향하는 간선의 수를 뜻합니다.
- 진입차수(in-degree) : 방향그래프에서 사용되는 용어로 외부 노드에서 들어오는 간선의 수를 뜻합니다.

- 그래프 구현방법

 
그래프를 구현하는 방법에는 인접행렬(Adjacency Materix)와 인접리스트(Adjacency List)방식이 있습니다. 두개의 구현 방식은 각각의 상반된 장단점을 가지고 있는데 대부분 인접리스트 형식을 많이들 사용합니다.




#### Direction graph

![Direction_graph](/images/direction_graph.png)

방향 그래프는 두 정점을 연결하는 간선에 방향이 존재하는 그래프입니다. 간선의 방향으로만 이동할 수 있습니다. 



#### Non-Direction graph

![Non-Direction_graph](/images/non_direction_graph.png)

무방향 그래프는 두 정점을 연결하는 간선에 방향이 없는 그래프입니다.



#### Adjacency matrix

![Adjacency_matrix](/images/adjacency_matrix.png)

인접행렬은 그래프의 노드를 2차원 배열로 만든 것입니다. 완성된 배열의 모양은 1, 2, 3, 4, 5, 6의 정점을 연결하는 노드에 다른 노드들이 인접 정점이라면 1, 아니면 0을 넣어줍니다.

- 장점
  1. 2차원 배열 안에 모든 정점들의 간선 정보를 담기 때문에 배열의 위치를 확인하면 두 점에 대한 연결 정보를 조회할 때 O(1) 의 시간 복잡도면 가능합니다. 
  2. 구현이 비교적 간편합니다.

- 단점
  1. 모든 정점에 대해 간선 정보를 대입해야 하므로 O(n²) 의 시간복잡도가 소요됩니다.
  2. 무조건 2차원 배열이 필요하기에 필요 이상의 공간이 낭비됩니다.


#### Adjacency list

![Adjacency_list](/images/adjacency_list.png)

인접리스트란 그래프의 노드들을 리스트로 표현한것입니다. 주로 정점의 리스트 배열을 만들어 관계를 설정해줌으로써 구현합니다. 

- 장점
  1. 정점들의 연결 정보를 탐색할 때 O(n) 의 시간이면 가능합니다. (n: 간선의 갯수)
  2. 필요한 만큼의 공간만 사용하기때문에 공간의 낭비가 적습니다.

 

- 단점
  1. 특정 두 점이 연결되었는지 확인하려면 인접행렬에 비해 시간이 오래 걸립니다. (배열보다 search 속도느림)
  2. 구현이 비교적 어렵습니다.


[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)

#### 그래프순회

그래프에의 임의의 한 정점에서 시작하여 모든 정점들을 한 번씩 방문하는 작업

- Search vs Traversal

  - 탐색(Search) : index나 해싱 등의 방법으로 원하는 데이터를 빠르게 찾는 방법
  - 순회(Traversal) : 특정 순회 알고리즘을 사용하여 모든 노드를 방문하는 방법

  - 탐색(search)의 관심 대상은 그래프 안의 특정 값(노드)이다. 그 관심 대상을 빠르게 찾는 검이 탐색의 목적이다.

  - 반면, 순회(traversal)는 특정 노드 뿐만이 아니라 모든 노드가 관심 대상이다. 즉, 그래프 자체가 순회의 관심 대상이다. 순회를 통해 특정 값을 찾는 것도 가능하고 그래프를 가공하는 것이 가능해진다. 

- 그래프 탐색(순회)은 왜 중요할까?

  - 그래프 탐색은 모든 정점을 방문하기 때문에 탐색을 통해 그래프 특징을 알 수 있다. 
  - 또한, 방문하면서 checking, update 등과 같은 처리가 가능하기 때문에 그래프를 가공할 수 있다. BFS, DFS와 같은 그래프 탐색 기법을 사용하면 스패닝 트리(Spanning Tree)를 구할 수 있다.
  - 즉, 탐색을 통해 (그래프 -> Spanning Tree 또는 MST - Minimu Spanning Tree)로 만들수 있다. 

##### 깊이우선탐색

- 자식 노드를 우선적으로 탐색하는 탐색 기법

- 아직 방문되지 않은 인접 노드(자식 노드)를 우선적으로 탐색

- 깊이 우선 탐색은 한쪽방향만 파다가 더이상 팔 곳이 없으면 다시 돌아와서 다른 한쪽을 죽어라 파는 형식이다.

- 깊이 우선 탐색은 Stack을 통해 구현된다.

- 그렇기 때문에 DFS를 구현할 떄 stack이나 재귀 함수를 사용할 수 있다.

- 재귀 함수를 사용하면 call stack을 사용하기 때문에 stack overflow를 조심해야 한다

- Spanning Tree, Connected Component, Strongly Connected Component 등에 활용

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

##### 너비우선탐색

- 형제 노드를 우선적으로 탐색하는 탐색 기법. (레벨 순회(level-order traversal)라고도 한다)

-  아직 방문되지 않은 이전 노드(부모 노드)의 인접 노드(현재 노드의 형제 노드)를 우선적으로 탐색

- BFS를 사용하면 매 탐색마다 휴리스틱 값을 찾아서 가장 최선의 휴리스틱 값의 노드로 확장이 가능하기 때문에 DFS대신 BFS가 최단 경로 탐색에 사용된다.

- 보통 너비 우선 탐색은 Queue를 통해 구현된다.

- 최단 경로 탐색, Spanning Tree, Connected Component, Strongly Connected Component 등에 활용

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
[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)



### 검색알고리즘

- 선형검색

* 직선으로 늘어선 배열에서 원하는 키값을 가진 원소를 찾을때까지 맨 앞부터 스캔하여 순서대로 검색하는 알고리즘
* 배열 원소의 개수가 n개라면, 조건을 판단하는 횟수는 평균 n/2번이다
* 값이 정렬되지 않은 배열에서 검색할때 사용하는 유일한 방법

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

- 보초법(Sentinel method) : 선형검색은 반복할때마다 2가지의 종료조건을 체크하므로, 이 비용을 반으로 줄이기 위한 방법
- 검색할 키값을 배열의 끝에 추가한 후, 찾은 값이 배열의 길이와 같으면 실패 반환

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

- 이진검색

* 사용하려면 배열의 데이터가 정렬되어있어야함
* 선형검색보다 빠르게 검색 가능하고 오름차순이나 내림차순에서 효율적으로 검색할 수 있음
* 찾아야 할 값과 검색범위의 중간지점값을 비교하여 검색범위를 반으로 줄여나감

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

- 해시법

* 검색과 함께 데이터의 추가, 삭제도 효율적으로 할 수 있음
* 데이터를 저장할 위치(인덱스)를 간단한 연산으로 구하는 방법
* 각각 배열의 키(원소의 값)을 배열의 원소 개수로 나눈 나머지(해시값)을 기준으로 데이터에 접근
* 해시테이블에서 만들어진 원소를 버킷이라고 함

```
Example

a = [5, 6, 14, 20, 29, 34, 37, 51, 69, 75, -, -, -]

원소의 개수 13으로 나눈 hash table에서 각 원소의 인덱스 번호 = 5, 6, 1, 7, 3, 8, 11, 12, 4, 10

hash_table_a = [-, 14, -, 29, 69, 5, 6, 20, 34, -, 75, 37, 51]

# 새로운 원소 35를 추가 : 35 % 13 = 9번 인덱스에 원소를 추가함 (원소의 이동이 필요없음)

```

- 해시법에서 저장할 곳에 이미 데이터가 들어있는 경우 2가지 방법으로 대체할 수 있다
  1. Chaining(Open hashing) : 해시값이 같은 원소를 연결 리스트로 관리
  2. Open addressing : 해시 충돌이 발생했을때 해시를 재실행 하여 빈 버킷을 찾음



### 스택과 큐

- 스택
- 큐

### 재귀알고리즘

- 함수안에서 함수 자신을 호출함
- 무한루프에 빠지기 쉽기때문에 종료조건을 꼭 지정해야함
- 모든 반복문은 재귀함수로 표현 가능

```
def f(n):
    if n > 1:
        return n * f(n-1)
    else:
        return 1

print(f(5))   >>> 120
```

### 정렬이론

- 버블정렬
- 단순선택정렬
- 단순삽입정렬
- 셀정렬
- 퀵정렬
- 병합정렬
- 힙정렬
- 도수정렬

### 문자열 검색

- 브루트 포스법
- KMP법
- 보이어-무어 법

### 리스트

### 트리와 그래프

### 깊이우선탐색과 너비우선탐색

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
