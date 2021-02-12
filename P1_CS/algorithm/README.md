# Algorithm

- [Basic Theory](#Basic-Theory)
- [Greedy Algorithm](#Greedy-Algorithm)

---

## Basic Theory

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
