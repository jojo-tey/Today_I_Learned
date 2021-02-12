## 함수

1. 함수는 이름으로 코드를 묶은것
2. 관리가 쉽고 재사용할 수 있음
3. 코드를 논리적으로 볼수 있도록 함
4. 함수의 리턴값을 정의하지 않으면 None 값이 자동으로 들어감

### 재귀함수

ㅊ

### 클로저

- 함수와 함께 독립적인 환경을 제공

```
def f():
    x = 10
    def xPlus():
        nonlocal x
        x += 10
        return x
    return xPlus

f1 = f()
f2 = f()

print(f1())   >> 20
print(f1())   >> 30
print(f2())   >> 20
```

<br>

## 클래스

### 클래스와 인스턴스

```
class Car(object):
    kinds = []
    def addkinds(self, name):
        self.kinds.append(name)
    maxSpeed = 300
    maxPeople = 5
    def move(self, x):
        print(x, 'km/h')
    def stop(self):
        print('Stopped')

m3 = Car()
x5 = Car()
m3.addkind('m3')
x5.addkind('x5')
print(k5.kinds)   >>> ['m3', 'x5']   # class variable
```

```
class Car(object):
    def __init__(self):
        print('instance created')
    def addkinds(self, name):
        self.kinds = []         # instance variable
        self.kinds.append(name)
    maxSpeed = 300
    maxPeople = 5
    def move(self, x):
        print(x, 'km/h')
    def stop(self):
        print('Stopped')

```

### 클래스의 상속

클래스의 오브젝트에 클래스를 넣어줌

Car = parentsclass(superclass)
Hybrid = childclass

```
class Hybrid(car):
    battery = 300
    batteryKM = 600

m3 = Car

```

### 내장함수(built-in functions)

dict
set
ort
등등
sort (리스트를 정렬시킴)
sorted (정렬된 값만 반환되고 직접 변하지는 않음)
lambda x : x \*\* 2 (lambda <input> : <output>)

- x가 들어오면 x의 제곱을 해라

name = ['a', 'b', 'c']
for i, j in enumerate(name, 100):
print (i, j)
인덱스와 같이 출력됨

### 파일 입출력

file = open('sample.txt', '<option>')
file.<method>('xxx')

file.close()

### 모듈 사용

다른 파일에 있는 클래스나 인스턴스, 변수 등을 가져옴

from people import name, age
from people import \*
