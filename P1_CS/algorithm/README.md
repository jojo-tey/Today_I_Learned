# Algorithm

- [Tips for Coding Interview](#Tips-for-Coding-Interview)
- [Interview Questions for Algorithms](#Interview-Questions-for-Algorithms)
- [Coding Exercises](#Coding-Exercises)
- [Strategic Approach to Problem Solving](#Strategic-Approach-to-Problem-Solving)
- [Theory](#Theory)
  - [Array](#array)
  - 스택
  - 큐
  - 해시테이블
  - 정렬
    - 선택정렬
    - 삽입정렬
    - 힙정렬
    - 퀵정렬
    - 병합정렬
  - 트리
    - BST (이진탐색트리)
    - 힙
    - 우선순위 큐
    - 이진힙
  - 그래프
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

배열을 사용하면 따로 흩어진 변수를 하나로 묶어서 사용할 수 있어 코드를 효율적으로 작성할 수 있다. 배열에는 객체가 저장되며 저장된 객체를 원소라고 한다. 또한 각 원소는 0부터 시작하는 인덱스를 가진다. 배열은 생성할 때 원소 개수를 자유롭게 지정할수 있다.
또한 배열에는 각각의 다른 자료형을 가질 수 있다. 


#### List / Tuple

파이썬의 경우 배열을 리스트와 튜플로 구현할 수 있다. 리스트와 튜플은 비슷하지만 원소의 변경가능 여부에 따라 차이가 있다. 

> - mutable : 리스트, 딕셔너리, 집합 등 (값 변경 가능)
> - immutable : 숫자, 문자열, 튜플 등 (값 변경 불가능)


리스트를 사용하면 1, 3, 5, 7, 9 숫자 모음을 다음과 같이 간단하게 표현할 수 있다.

```
>>> odd = [1, 3, 5, 7, 9]
```

리스트를 만들 때는 위에서 보는 것과 같이 대괄호([ ])로 감싸 주고 각 요솟값은 쉼표(,)로 구분해 준다.

리스트명 = [요소1, 요소2, 요소3, ...]
여러 가지 리스트의 생김새를 살펴보면 다음과 같다.

```
>>> a = []
>>> b = [1, 2, 3]
>>> c = ['Life', 'is', 'too', 'short']
>>> d = [1, 2, 'Life', 'is']
>>> e = [1, 2, ['Life', 'is']]
```


리스트는 a처럼 아무것도 포함하지 않아 비어 있는 리스트([ ])일 수도 있고 b처럼 숫자를 요솟값으로 가질 수도 있고 c처럼 문자열을 요솟값으로 가질 수도 있다. 또한 d처럼 숫자와 문자열을 함께 요솟값으로 가질 수도 있으며 e처럼 리스트 자체를 요솟값으로 가질 수도 있다. 즉 리스트 안에는 어떠한 자료형도 포함시킬 수 있다.



- 선형리스트


선형리스트(Linear List), 순서리스트(Ordered List)라고도 하는 선형리스트는, 리스트(List)의 두가지 종류중 하나입니다.

(리스트의) 크기가 처음부터 정적으로 정해져서, 데이터의 개수도 제한(고정)되있습니다. 

 

주로 (고정되어있는 크기의) 배열로 구현하는데요. 

그렇기에 원소 간에 순서가 있고, 각각의 요소에 인덱스를 사용할 수 있습니다.

따라서 원소 검색에서 효율적이지만, (인덱스로 바로 참조) 원소의 삽입과 삭제에서는 비효율적입니다. (하나의 삭제, 삽입에서 최악의 경우 기존의 모든 데이터를 이동해줘야 합니다)

선형리스트의 삽입에서는 두가지 경우가 있습니다.

삽입할 위치(인덱스)에 이미 값이 있냐 없냐인데요. 삽입할 위치가 값이없는, 빈공간이면 바로 원소를 삽입하면 되지만,

 

삽입할 위치에 이미 다른값이 있으면, 원래있는 값을 유지시키면서, 새로운 값을 삽입하도록 원래있는 값을 한칸 뒤로 밀어줘야합니다. (기존 인덱스의 바로 다음 인덱스로 값을 옮기는 것이죠) 

그런데 옮길 위치에도 이미 다른값이 존재한다면?  그렇기에 삽입할 위치로부터 마지막 원소까지 한칸씩 밀려쓴것처럼 해줘야 됩니다.  


선형리스트에서 삭제는 반대인데요,

맨 끝의 원소를 삭제하는 것은 괜찮지만, 맨끝 원소가 아니라면, 삭제후에 리스트 중간에 빈공간이 생깁니다.

그렇게되면...

그 빈공간을 다시 매꿀수 있게, 삭제할 인덱스 뒤의 있는 원소들을 앞으로 한칸씩 옮겨줘야 됩니다.
흔히 선형리스트의 삽입과 삭제는 차례대로 열을 맞춰서 서있는 것을 생각하면 쉽습니다.



- 연결리스트 

연결 리스트는 여러 개의 노드로 이루어져 있습니다. 각각의 노드는 데이터와 다음 노드가 뭔지 알려주는 주소를 가지고 있습니다. 또한 연결 리스트는 새로운 데이터를 추가하거나, 데이터의 위치를 찾거나, 제거하는 기능이 있어야 합니다.

1->2->3->4->5 라는 연결 리스트가 있다면 1,2,3,4,5는 데이터고 ->는 주소입니다. 안타깝게도, 이미 자바스크립트에는 이것이 구현되어 있습니다. 바로 배열입니다. [1,2,3,4,5]가 있으면 1,2,3,4,5는 데이터이고, array[0], array[1] 등은 데이터가 담긴 위치를 말해주고 있죠. 또한, array.push();를 통해 데이터를 추가할 수 있고, array.splice();를 통해 데이터를 제거할 수 있습니다. 

LinkedList에는 length와 head가 있습니다. length는 노드의 개수를 표현하는 부분이고, head가 바로 첫 노드의 주소를 가리키는 부분입니다. 

특수한 연결 리스트도 있습니다. 기본적인 연결 리스트는 한 쪽 방향으로만 이동합니다. 그래서 다시 뒤로 가기는 불편하죠. 이걸 해결한 리스트가 이중 연결 리스트입니다. next외에 this.prev를 넣어 이전 노드를 가리키게 한 겁니다. 구현은 조금 더 복잡해지지만, 한 번 구현하면 그 뒤로는 편하게 앞과 뒤로 노드를 왔다갔다할 수 있습니다. 또 지금은 하나의 데이터씩만 연결되지만 한 노드에서 여러 노드를 연결하는 다중 연결 리스트도 있습니다.




### 스택


스택은 실생활에도 많이 사용되는 자료구조 중 하나입니다. 연결 리스트인데 뒤로 넣고 뒤로만 뺄 수 있습니다. 앞으로는 넣지도, 빼지도 못합니다. 쉽게 생각하면 자바스크립트 배열인데 shift, unshift 없이 push와 pop만 있다고 생각하시면 됩니다. 사실 push와 pop이라는 메소드 이름이 스택에서 나온 겁니다. 또 한 가지의 메소드는 stackTop으로 스택의 마지막 요소를 알려주는 겁니다. 스택의 마지막 요소를 top이라고 부르기도 합니다.

실생활에서는 부엌에 있는 위아래로 쌓여진 접시들을 생각하면 편할 것 같습니다. 새로운 접시는 제일 위에 올리고, 접시를 사용할 때도 제일 위에서부터 꺼내죠? 프로그래밍 상에서도 스택이 자주 사용됩니다. 여러분은 stack overflow나 stack underflow라는 것을 들어보셨나요? stack overflow는 유명한 해외 프로그래밍 질의응답 커뮤니티이기도 하죠. 각각 주어진 스택 메모리보다 데이터를 더 넣었거나, 스택이 메모리가 비어있는데 거기서 데이터를 꺼내려고 했을 때 발생하는 대표적인 에러입니다. 실수로 재귀 함수를 무한 호출했을 때 stack overflow가 발생하죠.

재귀 함수를 호출하는 것과 stack overflow가 무슨 상관일까요? 바로 함수를 연이어 호출하면 스택처럼 메모리에 쌓이기(push) 때문입니다. 쌓인 역순으로 하나씩 실행됩니다(pop). 굳이 재귀 함수가 아니더라도 여러 함수가 중첩되어 호출되면 스택처럼 쌓입니다. 다만 재귀 함수를 사용했을 경우 stack overflow 에러가 자주 발생합니다.

```
py


stack = [1,2,3]
stack.append(4)

>>> stack 
# [1, 2, 3, 4]

top = stack.pop()
 
>>> print(top)
>>> stack
 
# 3
# [1, 2]


js

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

### 큐

큐는 실생활에서 줄이라고 생각하시면 됩니다. 우리가 순서를 기다릴 때 줄을 서죠? 새로 온 사람은 줄 맨 뒤에 서고, 제일 앞 사람은 필요한 행동을 한 후 빠집니다. 이렇게 뒤에서 들어가고(enqueue) 앞에서 빠지는(dequeue) 구조입니다. 자바스크립트의 배열로 따지면 push(enqueue)와 shift(dequeue) 메소드만 있는 거라고 생각하시면 됩니다. 거기에 추가로 제일 앞의 데이터를 알 수 있는 front가 있습니다.

스택에는 제일 위를 가리키는 top만 있었다면 큐에는 맨 처음을 가리키는 head와 맨 끝을 가리키는 rear 두 개가 있습니다.

특수한 큐도 있습니다. 순환 큐가 그 중 하나인데요. front와 rear가 연결되어 있습니다. 예를 들면 1, 2, 3의 데이터가 들어있는 큐가 있을 때 원래라면 3에서 끝나지만, 순환 큐는 rear인 3에서 다시 front인 1로 넘어갑니다. 코딩은 그냥 this.rear.next = this.front를 추가해주면 구현할 수 있습니다. 순환 큐가 사용되는 이유는 메모리 관리가 쉽기 때문인데 자바스크립트에서는 메모리를 알아서 정리해주기 때문에 그 효용성이 조금 떨어집니다. 

또 다른 큐로는 우선순위 큐가 있습니다. enqueue, dequeue는 같지만, enqueue할 때 제일 뒤에 넣는 게 아니라 우선순위 순서를 따져서 데이터를 넣습니다. 어떤 데이터가 우선순위가 높은지는 프로그래머가 직접 정해주면 됩니다. 문제는 우선순위 큐는 위와 같이 큐로 구현하면 데이터를 삽입하기 힘들다는 단점이 있습니다. 그래서 주로 힙이라는 자료구조를 사용해서 구한다.



- Using Queue in python


1. Deque in the collections module stands for double-ended queue, a data structure that allows data to be added and removed in both directions. The disadvantage is that the time complexity of random access is O(N). This is because it uses a linked list internally, and it takes i iterations from the front/back to access the i-th data.

2. Another way is to use the queue module's Queue class. This method is mainly used in a multi-threading environment, and it supports locking internally so that multiple threads can add or delete data at the same time. Unlike deque, since there is no direction, data addition and deletion are handled in one method. So, to add data, use the put(x) method, and to delete data use the get() method.


```
py



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


js

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

### 해시테이블



[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)
### 정렬

#### 선택정렬
#### 삽입정렬
#### 힙정렬
#### 퀵정렬
#### 병합정렬

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)

### 트리

#### BST (이진탐색트리)
#### 힙
#### 우선순위 큐
#### 이진힙

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)

### 그래프
#### 방향그래프
#### 무방향그래프
#### 인접행렬
#### 인접리스트


[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)

#### 그래프순회
##### 너비우선탐색(DFS)
##### 깊이우선탐색(BFS)




```
py





```









[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Algorithm)

### 검색알고리즘

- 선형검색

* 직선으로 늘어선 배열에서 원하는 키갚을 가진 원소를 찾을때까지 맨 앞부터 스캔하여 순서대로 검색하는 알고리즘
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
