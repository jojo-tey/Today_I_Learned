# Python

- [Generator](#generator)
- [Method execution when class is inherited](#Method-execution-when-class-is-inherited)
- [GIL and performance problems caused by it](#gil-and-performance-problems-caused-by-it)
- [How GC works](#How-GC-works)
- [Celery](#celery)
- [Why PyPy is faster than CPython](#Why-pypy-is-faster-than-cpython)
- [If memory leak may occur](#If-memory-leak-may-occur)
- [Duck Typing](#Duck-Typing)
- [Timsort](#Timsort)

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Python)

## Generator

[Generator](https://docs.python.org/3/tutorial/classes.html#generators) is the [iterator](https://docs.python) returned when the generator function is called. .org/3/tutorial/classes.html#iterators). Generator functions look like regular functions, but you can use `yield syntax' to return data at any point and resume processing. You can think of a general function as having one entry point, and a generator as having multiple entry points. Because of this characteristic, using a generator allows you to receive the desired data at the desired time.

### example

```
python
>>> def generator():
... yield 1
... yield'string'
... yield True

>>> gen = generator()
>>> gen
<generator object generator at 0x10a47c678>
>>> next(gen)
One
>>> next(gen)
'string'
>>> next(gen)
True
>>> next(gen)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
```

### action

1. Executing a generator function that contains a yield statement returns a generator object, but the contents of the function are not executed.
2. The generator can be executed through the built-in method called `next()`, and the `next()` method internally receives iterator as an argument and executes the `__next__()` method of the iterator.
3. When the `__next__()` method is called for the first time, the contents of the function are executed and processing stops when a yield statement is encountered.
4. At this time, all local state is maintained, including variable state, instruction pointer, internal stack, and exception handling state.
5. After that, control is yielded to the upper context, and when `__next__()` is called again, the generator restarts from the point where it stopped.

> The value of the yield statement differs depending on which method the generator was reactivated. If you use `__next__()`, it is None, and if you use `send()`, you have the value passed to the method and receive data from outside You will be able to.

### advantage

List, Set, and Dict expressions are iterable, so they can be useful in for expressions. While iterable objects are useful, they are not very good when dealing with large values ​​because they have to hold all the values ​​in memory. If you use a generator, you don't have to hold all the values ​​in memory because it receives and writes only the necessary values ​​through yield.

> The `range()` function returns a list in Python 2.x and a range object in Python 3.x. This range object is not a generator or iterator. In fact, when calling `next(range(1))`, the error `TypeError:'range' object is not an iterator` occurs. However, the internal implementation has an advantage in memory usage like using a generator.

```
python
>>> import sys
>>> a = [i for i in range(100000)]
>>> sys.getsizeof(a)
824464
>>> b = (i for i in range(100000))
>>> sys.getsizeof(b)
88
```

However, since the generator does not remember and throw the necessary values ​​at that moment, the `a list` can be used multiple times, whereas the `b generator` is exhausted after being used once. This is the same for all iterators. List and Set are iterable, but they are not iterators, so they are not exhausted.

```
python
>>> len(list(b))
100000
>>> len(list(b))
0
```

In addition, you can use the generator when there is infinite data to be provided with the `while True` statement, or it takes a lot of time to calculate all values ​​at once, and you want to receive and calculate only as much as you need.

### Relationship between Generator, Iterator, Iterable

![](http://nvie.com/img/relationships.png)

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Python)

## Method execution when class is inherited

Assuming that the instance method is executed, the method is executed after getting the bound method with `__getattribute__()`. The order in which methods are imported is according to `__mro__`. MRO (method resolution order) is the order of checking methods. Since Python 2.3, the C3 algorithm has been introduced and has been used until now. In the case of single inheritance or multiple inheritance, the order in which methods are accessed is stored in `__mro__` of the corresponding class. The higher the priority is to the left. There is a D class that has multiple inheritance of B and C, and when B and C each inherit A (diamond inheritance), as you can see if you search mro of D, the parent class must be located after the child class. If there is no appropriate method even after checking the top level object class, `AttributeError` is raised.

```
python
class A:
    pass

class B(A):
    pass

class C(A):
    pass

class D(B, C):
    pass

>>> D.__mro__
(__main__.D, __main__.B, __main__.C, __main__.A, object)
```

![](https://makina-corpus.com/blog/metier/2014/python-mro-conflict)

After Python 2.3, if you try to inherit the image above, you will get a `TypeError: Cannot create a consistent method resolution` error.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Python)

## GIL and performance problems caused by it

A performance problem arises due to GIL in the case of performing tasks (CPU bound) that have a large CPU impact on execution time, such as compression, sorting, and encoding, with multiple threads. At this time, because of the GIL, even if the work is performed with multiple threads, there is not much difference from the case of single thread. To solve this problem, multi-threads should be used for IO bound programs such as files and network IO, and multi-processes should be used.

### Global Interpreter Lock (GIL)

GIL is a concept that extends the lock used in threads to the interpreter level, and prevents multiple threads from executing simultaneously. More precisely, it forces only one bytecode to be executed at any point in time. Each thread can only run after waiting for the GIL to be released by another thread. In other words, even if it is made multi-threaded, it essentially operates as a single thread.

![](https://cdn-images-1.medium.com/max/1600/1*hqWXEQmyMZCGzAAxrd0N0g.png)

### Advantages of GIL

The number of cores is only increasing, and it seems that the advantages of this GIL are not fully utilized, but the advantages of this GIL also exist. Multi-thread using GIL is easier to implement than multi-thread that does not, and performance is superior to the _fine grained lock method_ when single-threaded because of less overhead thanks to GIL in the memory management method using reference counting. Also, when using C extension, GIL is released, so it may be faster if CPU bound program that uses C library is executed in multi-thread.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Python)

## How GC Works

By default in Python, [garbage collection](https://docs.python.org/3/glossary.html#term-garbage-collection)(garbage collection) and [reference counting](https://docs.python.org/3/glossary.html#term-reference-count) (reference counting) to manage the allocated memory. Basically, the reference counting method is used to release the object whose reference count is 0 from memory, but when the reference cycles (circular reference), which are not reachable but the reference count is not 0, occurs, the situation is solved by garbage collection. do.

> Strictly speaking, the act of releasing an object from memory through the reference counting method is a form of garbage collection, but here, when a cyclic reference occurs, garbage collection through the cyclic garbage collector and garbage collection through the reference counting. Separated collections.

Here,'How do you detect circular reference occurrences?','If you monitor periodically, what is the criterion for that period?','When does garbage collection occur?' The same question may be asked, but before addressing this question, let's briefly move on to some simple concepts of reference counting, circular reference, and Python's garbage collector. If you know this concept, you can read the [How Garbage Collection Works] (#Garbage-Collection-Work-How).

#### Reference counting

Every object increments the reference counter when it is referenced and decrements it when the reference is gone. When this counter reaches zero, the object is released from memory. If you want to see the reference count of an object, you can check it with `sys.getrefcount()`.

<details>
    <summary>
        Counter increment/decrement through <code>Py_INCREF()</code> and <code>Py_DECREF()</code>
    </summary>
<br>

The command to increase or decrease the counter is declared in [object.h](https://github.com/python/cpython/blob/master/Include/object.h) as follows. When increasing the counter, simply use `ob_refcnt`. When incrementing and decrementing by 1, it decrements by 1, and when the counter reaches 0, the object is released from memory.

```
c
#define Py_INCREF(op) (\
    _Py_INC_REFTOTAL _Py_REF_DEBUG_COMMA \
    ((PyObject *)(op))->ob_refcnt++)

#define Py_DECREF(op) \
    do {\
        PyObject *_py_decref_tmp = (PyObject *)(op); \
        if (_Py_DEC_REFTOTAL _Py_REF_DEBUG_COMMA \
        --(_py_decref_tmp)->ob_refcnt != 0) \
            _Py_CHECK_REFCNT(_py_decref_tmp) \
        else \
            _Py_Dealloc(_py_decref_tmp); \
    } while (0)
```

For more accurate information, refer to [Python official documentation](https://docs.python.org/3/extending/extending.html#reference-counting-in-python).

</details>

#### circular reference

A simple example of a circular reference is an object that refers to itself.

```
python
>>> l = []
>>> l.append(l)
>>> del l
```

The reference count of `l` is 1, but this object is no longer accessible and cannot be freed from memory using the reference counting method.

Another example is objects that refer to each other.

```
python
>>> a = Foo() # 0x60
>>> b = Foo() # 0xa8
>>> a.x = b # The x of 0x60 points to 0xa8.
>>> b.x = a # x in 0xa8 points to 0x60.
# At this point, the reference counter of 0x60 is 2
# 0xa8's reference counter is 2 with b and a.x.
>>> del a # 0x60 decreases to 1. 0xa8 is 2 as b and 0x60.x.
>>> del b # 0xa8 also decreases to 1.
```

In this state, since `0x60.x` and `0xa8.x` refer to each other, the reference count is both 1, but it becomes unreachable garbage.

#### garbage collector

You can directly control the garbage collector through Python's `gc` module. The `gc` module supports [cyclic garbage collection](https://docs.python.org/3/c-api/gcsupport.html), which can solve reference cycles (refer to circulation). The gc module exists only to detect and resolve circular references. Disable the garbage collector via `gc.disable()` if you can be sure that the [`gc` official Python documentation](https://docs.python.org/3/library/gc.html) does not make circular references. It is mentioned that it can be done.

> Since the collector supplements the reference counting already used in Python, you can disable the collector if you are sure your program does not create reference cycles.

### How Garbage Collection Works

How the cyclic garbage collection, which can also resolve the cyclic reference state, operates is about **by what criteria garbage collection occurs** and **how to detect cyclic references**. Let's look at this step by step.

#### How does garbage collection occur?

The question raised earlier is, in the end, a question about the accrual criteria. The garbage collector internally manages the garbage collection cycle and objects with `generation` and `threshold` (threshold). Generations are divided into generation 0, generation 1, and generation 2. Recently created objects enter generation 0 (young), and older objects exist in generation 2 (old). In addition, an object belongs to only one generation. The garbage collector is designed to garbage collection more frequently in generation 0, which is based on the [generational hypothesis](http://www.memorymanagement.org/glossary/g.html#term-generational-hypothesis).

<details>
    <summary>Two hypotheses for the generational hypothesis</summary>
<br>

- Most objects quickly become unreachable.
- There are very few references from old to young objects.

![](https://plumbr.io/wp-content/uploads/2015/05/object-age-based-on-GC-generation-generational-hypothesis.png)
<sup> _Source [plumbr.io](https://plumbr.io/handbook/garbage-collection-in-java/generational-hypothesis)_ </sup>

<hr>
</details>

The period is related to the threshold, which can be checked with `gc.get_threshold()`.

```python
>>> gc.get_threshold()
(700, 10, 10)
```

It means `threshold 0`, `threshold 1`, and `threshold 2`, respectively. When the number of times the object is allocated to generation n exceeds `threshold n`, garbage collection is performed and this value can be changed.

In the case of generation 0, it is executed when the number of objects is subtracted from the number of times the object is allocated to the memory, that is, the number of objects exceeds `threshold 0`. However, it is slightly different from the subsequent generations. After the generation 0 garbage collection occurs, the generation 0 object is moved to generation 1 and the counter is incremented by 1. If this generation 1 counter exceeds `threshold 1`, then generation 1 garbage collection occurs. To put it roughly, if a generation 0 garbage collection occurs only 700 object creation times, it means that the first generation occurs only 7,000 times, and the second generation occurs 70,000 times.

To explain this in words, it got a little complicated, but in simple terms, `generation[0].count++` occurs when memory is allocated, `generation[0].count--` occurs when memory is allocated, and `generation[0].count> threshold[0 ]`, `genreation[0].count = 0`, `generation[1].count++` occurs. When `generation[1].count> 10`, the 0 generation and 1 generation count are set to 0 and `generation[ 2].count++`.

[View with gcmodule.c code](https://github.com/python/cpython/blob/master/Modules/gcmodule.c#L832-L836)

#### life cycle

In this way, the garbage collector manages the cycle of garbage collection through generations and thresholds. Before we start looking at how the garbage collector finds circular references, let's take a quick look at the garbage collection's execution process (life cycle).

When a new object is created, Python allocates the object to memory and generation 0. If the number of generation 0 objects is greater than `threshold 0`, `collect_generations()` is executed.

<details>
    <summary>More detailed explanation with code</summary>
<br>

When a new object is created, Python calls `_PyObject_GC_Alloc()`. This method allocates an object to memory and increments the garbage collector's generation 0 counter. Next, check whether the number of objects in generation 0 is greater than `threshold 0`, whether `gc.enabled` is true, whether `threshold 0` is not 0, and not in garbage collection, and if all conditions are satisfied, `collect_generations()` is executed. Run.

The following is a simplified source of `_PyObject_GC_Alloc()`, and the entire method can be found in [here](https://github.com/python/cpython/blob/master/Modules/gcmodule.c#L1681-L1710) .

```
c

_PyObject_GC_Alloc() {
    // ...

    gc.generations[0].count++; /* Generation 0 counter increment */
    if (gc.generations[0].count> gc.generations[0].threshold && /* threshold is exceeded */
        gc.enabled && /* enabled and */
        gc.generations[0].threshold && /* Threshold is not zero */
        !gc.collecting) /* If not in collection */
    {
        gc.collecting = 1;
        collect_generations();
        gc.collecting = 0;
    }
    // ...
}
```

For reference, if you want to turn off `gc`, `gc.set_threshold(0)` is more obvious than `gc.disable()`. In the case of `disable()`, it is said that there are cases of `enable()` in a third party library.

<hr>
</details>

When `collect_generations()` is called, all generations (basically 3 generations) are checked, starting with the oldest generation (2nd generation). If the number of times the object is allocated to the corresponding generation is greater than the `threshold n` corresponding to each generation, `collect()` is called to perform garbage collection.

<details>
    <summary>code</summary>
<br>

When `collect()` is called, all generations younger than the corresponding generation are integrated and garbage collection is performed, so the check is stopped through `break`.

The following is a simplified source of `collect_generations()`, and the entire method can be found in [Here](https://github.com/python/cpython/blob/master/Modules/gcmodule.c#L1020-L1056) .

```
c

static Py_ssize_t
collect_generations(void)
{
    int i;
    for (i = NUM_GENERATIONS-1; i >= 0; i--) {
        if (gc.generations[i].count> gc.generations[i].threshold) {
            collect_with_callback(i);
            break;
        }
    }
}

static Py_ssize_t
collect_with_callback(int generation)
{
    // ...
    result = collect(generation, &collected, &uncollectable, 0);
    // ...
}
```

<hr>
</details>

The `collect()` method performs the **circular reference detection algorithm**, distinguishes between reachable and unreachable objects in a specific generation, and finds a set of unreachable objects. The set of reachable objects is merged into the next higher generation (moved to generation 1 if performed in generation 0), and the set of unreachable objects is released from memory after performing a callback.

#### How to detect circular references

First, it should be noted that circular references can only be generated by container objects (e.g. `tuple`, `list`, `set`, `dict`, and `class`). Container objects can hold references to other objects. Therefore, you can focus your attention only on container objects, ignoring integers and strings.

The idea to resolve circular references is to keep track of all container objects. There are many ways, but it is best to use a double linked list for the link field inside the object. This allows you to quickly add and remove objects from the **container object set** without any additional memory allocation. When a container object is created, it is added to this set, and when it is removed, it is removed from the set.

<details>
    <summary>
        Double linked list declared in <code>PyGC_Head</code>
    </summary>
<br>

The double linked list is declared as follows and can be checked in [objimpl.h code](https://github.com/python/cpython/blob/master/Include/objimpl.h#L250-L259)

```
c

#ifndef Py_LIMITED_API
typedef union _gc_head {
    struct {
        union _gc_head *gc_next;
        union _gc_head *gc_prev;
        Py_ssize_t gc_refs;
    } gc;
    double dummy; /* force worst-case alignment */
} PyGC_Head;
```

<hr>
</details>

Now that you have access to all container objects, you should be able to find the circular reference. The process of finding a circular reference is as follows.

1. Set the `gc_refs` field in the object equal to the reference count.
2. Find the other container objects referenced by each object, and decrement the `gc_refs` of the referenced container.
3. If `gc_refs` is 0, it means that the object refers to each other within the container set.
4. Mark the object as unreachable and release it from memory.

Now we know how the garbage collector detects circular reference objects and frees them from memory.

#### example

> The example below is an easy-to-see example and is different from the actual `collect()` operation. The exact operation is described again below. Or refer to [`collect()` code](https://github.com/python/cpython/blob/master/Modules/gcmodule.c#L797-L981).

In the example below, we will see how the garbage collector frees the circular reference objects `Foo(0)` and `Foo(1)`.

```python
a = [1]
# Set: a:[1]
b = ['a']
# Set: a:[1] <-> b:['a']
c = [a, b]
# Set: a:[1] <-> b:['a'] <-> c:[a, b]
d = c
# Set: a:[1] <-> b:['a'] <-> c,d:[a, b]
# Since the container object was not created, only the reference count is increased.
e = Foo(0)
# Set: a:[1] <-> b:['a'] <-> c,d:[a, b] <-> e:Foo(0)
f = Foo(1)
# Set: a:[1] <-> b:['a'] <-> c,d:[a, b] <-> e:Foo(0) <-> f:Foo(1)
e.x = f
# Set: a:[1] <-> b:['a'] <-> c,d:[a, b] <-> e:Foo(0) <-> f,Foo(0).x :Foo(1)
f.x = e
# Set: a:[1] <-> b:['a'] <-> c,d:[a, b] <-> e,Foo(1).x:Foo(0) <-> f ,Foo(0).x:Foo(1)
del e
# Set: a:[1] <-> b:['a'] <-> c,d:[a, b] <-> Foo(1).x:Foo(0) <-> f,Foo (0).x:Foo(1)
del f
# Set: a:[1] <-> b:['a'] <-> c,d:[a, b] <-> Foo(1).x:Foo(0) <-> Foo(0 ).x:Foo(1)
```

In the above situation, the reference count of each container object is as follows.

```
py
# ref count
[1] <- a,c = 2
['a'] <- b,c = 2
[a, b] <- c,d = 2
Foo(0) <- Foo(1).x = 1
Foo(1) <- Foo(0).x = 1
```

In step 1, the `gc_refs` of each container object is set.

```
py
# gc_refs
[1] = 2
['a'] = 2
[a, b] = 2
Foo(0) = 1
Foo(1) = 1
```

In step 2, the container set is traversed and `gc_refs` is decreased.

```
py
[1] = 1 # Decrease by 1 since it is referenced by [a, b]
['a'] = 1 # Decrease by 1 since it is referenced by [a, b]
[a, b] = 2 # As it is not referenced
Foo(0) = 0 # Decrease by 1 since it is referenced by Foo(1)
Foo(1) = 0 # Decrease by 1 since it is referenced by Foo(0)
```

Through step 3, a circular reference object whose `gc_refs` is 0 was found. Now let's move this object into an unreachable set.

```
py
 unreachable | reachable
             | [1] = 1
 Foo(0) = 0 | ['a'] = 1
 Foo(1) = 0 | [a, b] = 2
```

Now, when `Foo(0)` and `Foo(1)` are released from memory, the garbage collection process ends.

### More accurate and detailed explanation

The `collect()` method combines the current and young generations to check for circular references. The combined generation is named `young`, and finally the unreachable list of unreachable objects is released from memory through the following process, and the object remaining in young is allocated to the next generation.

```c
update_refs(young)
subtract_refs(young)
gc_init_list(&unreachable)
move_unreachable(young, &unreachable)
```

`update_refs()` makes a copy of the reference count of all objects. This is to prevent the garbage collector from touching the actual reference count.

`subtract_refs()` decrements the `gc_refs` of object j referenced by i for each object i. At the end of this process, the (remaining object reference count in the young generation)-(remaining `gc_refs`) is equal to the number referring to the young generation in the old generation.

The `move_unreachable()` method scans the young generation, moves the object whose `gc_refs` is 0 to the `unreachable` list, and sets `GC_TENTATIVELY_UNREACHABLE`. The reason why it is set tentatively rather than completely `unreachable` is that it may be reached from the object to be scanned later.

<details>
    <summary>View an example</summary>
<br>

```
py
a, b = Foo(0), Foo(1)
a.x = b
b.x = a
c = b
del a
del b

# Summarizing the above situation is as follows.
Foo(0).x = Foo(1)
Foo(1).x = Foo(0)
c = Foo(1)
```

At this time, the situation is as follows. Even if `gc_refs` of `Foo(0)` is 0, it can be reached through `Foo(1)` that follows.

|  young   | ref count | gc_refs | reachable |
| :------: | :-------: | :-----: | :-------: |
| `Foo(0)` |     1     |    0    |   `c.x`   |
| `Foo(1)` |     2     |    1    |    `c`    |

<hr>
</details>

An object other than 0 is set to `GC_REACHABLE`, and the object referenced by the object is traversed and set to `GC_REACHABLE`. If the object was in the `unreachable` list, it is sent to the end of the `young` list. The reason why it is sent to the end of `young` is that the object may also refer to another object whose `gc_refs` is 0.

<details>
    <summary>View example</summary>
<br>

```
py
a, b = Foo(0), Foo(1)
a.x = b
b.x = a
c = b
d = Foo(2)
d.x = d
a.y = d
del d
del a
del b

# Summarizing the above situation is as follows.
Foo(0).x = Foo(1)
Foo(1).x = Foo(0)
c = Foo(1)
Foo(0).y = Foo(2)
```

|  young   | ref count | gc_refs | reachable |
| :------: | :-------: | :-----: | :-------: |
| `Foo(0)` |     1     |    0    |   `c.x`   |
| `Foo(1)` |     2     |    1    |    `c`    |
| `Foo(2)` |     1     |    0    |  `c.x.y`  |

In this situation, `Foo(0)` was in the `unreachable` list, and then returned to the end of the `young` list by examining `Foo(1)`, and `Foo(2)` also went to the `unreachable` list. Soon, knowing that it can be referenced by `Foo(0)`, it comes back to the `young` list.

<hr>
</details>

After a full scan of the `young` list is complete, objects in the `unreachable` list are now **really unreachable**. Now these objects are freed from memory and the objects in the `young` list are merged into the higher generation.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Python)

## Celery

[Celery](https://docs.celeryproject.org/en/stable/) is a message-passing distributed asynchronous work queue. The task is delivered to the worker as a message through the broker and processed. Tasks can be executed concurrently on one or more workers using multiprocessing, eventlets, and gevents, and can be executed asynchronously in the background.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Python)

<br>

## Why PyPy is faster than CPython

In short, CPython is a general interpreter, whereas PyPy is an interpreter that provides [Execution Trace JIT (Just In Time) Compilation](https://en.wikipedia.org/wiki/Tracing_just-in-time_compilation). PyPy is an interpreter compiled with RPython. It is a RPython toolchain written in C, and it has a faster execution speed than CPython by adding hints for JIT compilation to the interpreter source.

### PyPy

PyPy is a Python interpreter written in Python. In general, I think it will be very slow because the Python interpreter is implemented in Python once again, but PyPy is actually faster than CPython as you can see in [Speed ​​Center](http://speed.pypy.org/).

### Execution Trace JIT Compilation

Unlike traditional JIT, which optimizes by method, it optimizes loops that are frequently executed at runtime.

### RPython (Restricted Python)

[RPython](https://rpython.readthedocs.io/en/latest/index.html) implements this execution tracking JIT compilation in C to include the toolchain. So, if you write an interpreter in RPython and add hints to the toolchain, it builds the execution trace JIT compiler in the interpreter. For reference, RPython is a kind of interpreter production framework (language) created by the PyPy project team. In Python, a dynamic language, RPython was created to allow static compilation of variables by imposing restrictions on the standard library and grammar, and it is used to implement a dynamic language interpreter.

By separating language specifications (Python language rules, BF language rules, etc.) and implementation (production of actual interpreters) in this way, it is possible to automatically generate just-in-time (JIT) compilers for any dynamic language.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Python)

## If memory leak may occur

It depends a little bit on how you define the memory leak. After declaring `a = 1`, you can see this as a memory leak even if your program no longer uses `a`. However, only memory leaks caused by user carelessness are mentioned here.

Typically, a memory leak occurs when a mutable object is used as the default parameter value.

```
python
def foo(a=[]):
    a.append(time.time())
    return a
```

In the above case, each time `foo()` is called, a timestamp value is added to `a`, the default parameter value. This can lead to unintended results, so in the normal case, `a=None` is set and an empty list is allocated with `if a is None` syntax inside the function.

As another case, consider cached data without timeout in a web application. As requests come in, cache data only accumulates, but if you do not create a separate routine to release them, this will also cause a memory leak.

Redefining the `__del__` method in a class can also cause a memory leak. If the class being circularly referenced overrides the `__del__` method, it is not freed by the garbage collector.

- [Is it possible to have an actual memory leak?](https://stackoverflow.com/questions/2017381/is-it-possible-to-have-an-actual-memory-leak-in-python-because-of-your-code)

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Python)

## Duck Typing

Duck typing is a concept commonly used in programming languages ​​that have dynamic types, and it means that variables and methods of an object determine the suitability of the object rather than the actual type of the object. The term Duck typing comes from a phrase commonly called [duck test](https://en.wikipedia.org/wiki/Duck_test).

> If it walks like a duck and it quacks like a duck, then it must be a duck.
>
> If the bird walks like a duck and quacks like a duck, it will be a duck.

Python, which is a dynamic typed language, does not perform type checking when calling a method or accessing a variable, so duck typing can be used in a wide range.
The following is an example of simple duck typing.

```
py
class Duck:
    def walk(self):
        print('Whipped back')

    def quack(self):
        print('Quack!')

class Mallard: # Mallard
    def walk(self):
        print('Don't')

    def quack(self):
        print('Quaaack!')

class Dog:
    def run(self):
        print('Tadadada')

    def bark(self):
        print('walwal')


def walk_and_quack(animal):
    animal.walk()
    animal.quack()


walk_and_quack(Duck()) # prints'Quack!', prints'Quack!'
walk_and_quack(Mallard()) # prints'Quaaack!', prints'Quaaack!'
walk_and_quack(Dog()) # AttributeError:'Dog' object has no attribute'walk'
```

In the example above, both `Duck` and `Mallard` implement `walk()` and `quack()`, so they are **suitable** as arguments to the function `walk_and_quack()`.
However, since both methods are not implemented, `Dog` is inappropriate as an argument to the function. In other words, `Dog` fails proper duck typing.

In Python, duck typing is used in various places. Implement `__len__()` to express _something of length_ (commonly expressed as [listy](https://cs.gmu.edu/~kauffman/cs310/w04-2.pdf)), Alternatively, implement `__iter__()` and `__getitem__()` to duck-typing [iterable](https://docs.python.org/3/glossary.html#term-iterable).
If you implement `__iter__()` and `__getitem__()` without inheriting the interface `Iterable` (pseudonym), you can use it directly in `for ... in`.

In general, this is a way to implement `interface` or inherit a class.
It is compared with statically typed languages ​​that determine the suitability of arguments or variables before runtime.
In Java and Scala, `interface` and c++ use `template` to ensure type conformance.
(In the case of c++, `template` can have the same effect as duck typing [Reference](http://www.drdobbs.com/templates-and-duck-typing/184401971))

</br>

## Timsort

> Python's internal sort

Python's internal sort is implemented with the timsort algorithm.
It has been applied since version 2.3, and is a stable sort in which merge sort and insert sort are merged.

timsort guarantees the worst time complexity of merge sort and the highest time complexity of insert sort. Therefore, the temporal complexity of O(n) ~ O(n log n) can be guaranteed, and even in the case of spatial complexity, it has a spatial complexity of O(n) in the worst case. In addition, the order of elements with the same key is not mixed with the stable alignment.

For a more detailed understanding of timsort, refer to [python listsort](https://github.com/python/cpython/blob/24e5ad4689de9adc8e4a7d8c08fe400dcea668e6/Objects/listsort.txt).

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Python)

_python.end_
