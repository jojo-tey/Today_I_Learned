# Algorithm

- [Tips for Coding Interview](#Tips-for-Coding-Interview)
- [Interview Questions for Algorithms](#Interview-Questions-for-Algorithms)
- [Coding Exercises](#Coding-Exercises)
- [Strategic Approach to Problem Solving](#Strategic-Approach-to-Problem-Solving)
- [Theory](#Theory)
  - 배열
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
