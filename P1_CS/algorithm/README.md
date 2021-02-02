# Algorithm

* [Greedy Algorithm](#Greedy-Algorithm)


---



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

Given a string S consisting of only numbers (0 to 9) each digit. Check all numbers one by one from left to right, and puts the'*' or'+' operator between the numbers to create the largest number that can be made. However, it is assumed that all operations are performed in order from left to right.
Create a program that fits the above conditions

> For example, the largest number that can be made with the string 02984 is ((((0 + 2) * 9) * 8) * 4) = 576. Also, the input value is given so that the largest number that can be made is always an integer less than 2 billion.


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





