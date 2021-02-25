# JavaScript

- [JavaScript Event Loop](#javascript-event-loop)
- [Hoisting](#hoisting)
- [Closure](#closure)
- [About this](#about-this)
- [Promise](#promise)
- [Arrow Function](#arrow-function)

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#JavaScript)

## JavaScript Event Loop

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#JavaScript)

## Hoisting

\_As the ES6 grammar became standardized, it became a part that we didn't need to pay much attention to, but it is one of the characteristics that best shows the characteristics of a language called JavaScript.

### Justice

The dictionary definition of the word `hoist` means to raise. What is pulled up in JavaScript are variables All variable declarations declared with the `var` keyword are **hosted**. Hoist means that the definition of a variable is divided into `declaration` and `assignment` according to its scope. In other words, if a variable is defined in a function, the declaration is changed to the top level of the function, and if it is defined outside the function, it is changed to the top level of the global context.

First of all, you need to understand Declaration and Assignment. What is raised is a declaration.

```
js
function getX() {
  console.log(x); // undefined
  var x = 100;
  console.log(x); // 100
}
getX();
```

For other languages, if you try to print the variable x without declaring it, you will get an error. However, in JavaScript, it is called `undefined`. This is because `var x = 100;` hoists `var x;` in this syntax. That is, if you reorganize the code according to the order of operation, it is as follows.

```
js
function getX() {
  var x;
  console.log(x);
  x = 100;
  console.log(x);
}
getX();
```

Declarations are always interpreted as the top priority when the JavaScript engine is running, so they are hoisted.

Regardless of the code in which the function is located, the scope of the function defined in the form of a function declaration starts from the beginning of the entire code. This means that the JavaScript engine raises the function declaration even if the function declaration is behind the function execution part. Function hoisting raises the function, but not the value of the variable.

```
js
foo( );
function foo( ){
  console.log('hello');
};
// console> hello
```

Because the declaration for the foo function is hoisted and registered in the global object, `hello` is properly displayed.

```
js
foo( );
var foo = function() {
  console.log('hello');
};
// console> Uncaught TypeError: foo is not a function
```

The function expression in this second example is not hoisted because it is a structure that allocates function literals, and therefore, generates `Type Error` in the runtime environment.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#JavaScript)

## Closure

Closure is a kind of special object made up of **environment made of two functions** Here, **environment** refers to the `context` that includes several local variables in the **scope** when the closure is created. Through this closure, it is possible to provide a plan to implement private properties/methods and public properties/methods that are not in JavaScript.

### Creating Closures

The following are the conditions under which closures are created.

1. The inner function becomes an anonymous function and is used as the return value of the outer function.
2. The inner function is executed in the execution environment of the outer function.
3. The variable x used in the inner function is in the variable scope of the outer function.

```
js
function outer() {
  var name = `closure`;
  function inner() {
    console.log(name);
  }
  inner();
}
outer();
// console> closure
```

It can be seen that the variable `name` does not exist in the `context` that executes the `outer` function. In a similar vein, you can make some changes to the code.

```
js
var name = `Warning`;
function outer() {
  var name = `closure`;
  return function inner() {
    console.log(name);
  };
}

var callFunc = outer();
callFunc();
// console> closure
```

In the code above, `callFunc` is called a closure. The value of `name` is printed on the console by calling `callFunc`, but the value printed is not `Warning`, but `closure`. In other words, it refers to a variable belonging to the context of the `outer` function. Here, the `name` variable that exists as a local variable of the `outer` function is called `free variable`.

Even if the external function call is terminated, a structure that can maintain the chain relationship between the local variable of the external function and the variable scope object is called a closure. More precisely, it refers to an inner function returned by an outer function.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#JavaScript)

## About this

In JavaScript, every time a function is executed, an object called `this` is added inside the function. It is implicitly passed into the function with a pseudo array object called `arguments`. Therefore, `this` in JavaScript changes its appearance depending on the situation in which the function is called.

### Situation 1. When calling a method of an object

When an object property is a function, it is called a method. `this` refers to the object that owns the function (the instance containing the method) when executing the function. That is, it is bound to the object that called the method. In case of `A.B`, `this` in `B` function refers to `A`.

```
js
var myObject = {
  name: "foo",
  sayName: function() {
    console.log(this);
  }
};
myObject.sayName();
// console> Object {name: "foo", sayName: sayName()}
```

</br>

### Situation 2. When calling a function

When a function is called rather than a method of a specific object, this used in the code inside the function is bound to the global object. In case of `A.B`, `A` becomes a global object, so `this` in `B` function is bound to the global object of course.

```
js
var value = 100;
var myObj = {
  value: 1,
  func1: function() {
    console.log(`func1's this.value: ${this.value}`);

    var func2 = function() {
      console.log(`func2's this.value ${this.value}`);
    };
    func2();
  }
};

myObj.func1();
// console> func1's this.value: 1
// console> func2's this.value: 100
```

`this` in `func1` is the same as **situation 1**. Therefore, `myObj` is bound to `this` and the `value` of `myObj`, 1, is printed on the console. But `func` should be interpreted as **Situation 2**. Since there is no `A` in `A.B` structure, `this` refers to the global object inside the function, and `value` becomes 100.

</br>

### Situation 3. When creating an object through a constructor function

When calling the constructor function through the `new` keyword instead of just calling a function, `this` is also bound differently. Inside a function called through the keyword `new`, `this` becomes the object itself. The binding of `this` when calling a constructor function can be understood through the way the constructor function behaves.

When a function is called as a constructor through the `new` operator, an empty object is created and this is bound. This object is an object created through a function, and is connected to its parent, the prototype object. And if the return statement is not specified, the newly created object bound to `this` is returned.

```
js
var Person = function(name) {
  console.log(this);
  this.name = name;
};

var foo = new Person("foo"); // Person
console.log(foo.name); // foo
```

</br>

### Situation 4. Call through apply, call, bind

This is a way to inject or set `this` as JavaScript code without relying on situation 1, situation 2, or situation 3. Let's look at the example code we used in situation 2 again. When calling `func2`, the above three methods can be used to inject this in `func1`. And in order to understand the difference between the three methods, it is modified to receive parameters in `func2`.

- Use `bind` method

```
js
var value = 100;
var myObj = {
  value: 1,
  func1: function() {
    console.log(`func1's this.value: ${this.value}`);

    var func2 = function(val1, val2) {
      console.log(`func2's this.value ${this.value} and ${val1} and ${val2}`);
    }.bind(this, `param1`, `param2`);
    func2();
  }
};

myObj.func1();
// console> func1's this.value: 1
// console> func2's this.value: 1 and param1 and param2
```

- Use `call` method

```
js
var value = 100;
var myObj = {
  value: 1,
  func1: function() {
    console.log(`func1's this.value: ${this.value}`);

    var func2 = function(val1, val2) {
      console.log(`func2's this.value ${this.value} and ${val1} and ${val2}`);
    };
    func2.call(this, `param1`, `param2`);
  }
};

myObj.func1();
// console> func1's this.value: 1
// console> func2's this.value: 1 and param1 and param2
```

- Use `apply` method

```
js
var value = 100;
var myObj = {
  value: 1,
  func1: function() {
    console.log(`func1's this.value: ${this.value}`);

    var func2 = function(val1, val2) {
      console.log(`func2's this.value ${this.value} and ${val1} and ${val2}`);
    };
    func2.apply(this, [`param1`, `param2`]);
  }
};

myObj.func1();
// console> func1's this.value: 1
// console> func2's this.value: 1 and param1 and param2
```

- `bind` vs `apply`, `call`
  First of all, `bind` can specify `this` and parameters when declaring a function, and `call` and `apply` specify `this` and parameters when calling a function.

- `apply` vs `bind`, `call`
  Pass `this` as the first argument to the `apply` method, and the parameters to be passed as the second argument in the form of an array. The `bind` method and the `call` method pass each parameter one by one.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#JavaScript)

## Promise

In Javascript, most tasks are done asynchronously. It was a problem that could be handled with a callback function, but these days, as the size of the front end increases, there has been a situation where the complexity of the code increases. At the same time, a case of overlapping callbacks occurred accordingly, and the Promise pattern emerged as a solution to this. Using the Promise pattern makes it easier to control asynchronous tasks such as sequentially or in parallel. Also, because there is a structure for exception handling, error handling can be managed more visually. This Promise pattern was formally included in the ECMAScript6 specification.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#JavaScript)

## Async/Await

It's a new way to write asynchronous code. Javascript developers weren't satisfied with the promise of a good asynchronous processing method, and devised a better way (in fact, async/await is based on promises). Like code written in procedural languages, it is simple to use and easy to understand. Just put async in front of the function keyword and await in front of the asynchronous processing function that returns the promise inside the function. The biggest advantage of async/await is that it makes the appearance of asynchronous code cleaner than Promise. This is the official specification of es8 and is supported by node8LTS (it says Babel supports async/await so you can use it right away!)

- Implemented as `promise`

```
js
function makeRequest() {
    return getData()
        .then(data => {
            if(data && data.needMoreRequest) {
                return makeMoreRequest(data)
                  .then(moreData => {
                      console.log(moreData);
                      return moreData;
                  }).catch((error) => {
                      console.log('Error while makeMoreRequest', error);
                  });
            } else {
                console.log(data);
                return data;
            }
        }).catch((error) => {
          console.log('Error while getData', error);
        });
}
```

- Implementation of `async/await`

```
js
async function makeRequest() {
    try {
      const data = await getData();
      if(data && data.needMoreRequest) {
          const moreData = await makeMoreRequest(data);
          console.log(moreData);
          return moreData;
      } else {
          console.log(data);
          return data;
      }
    } catch (error) {
        console.log('Error while getData', error);
    }
}
```

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#JavaScript)

## Arrow Function

Arrow function expressions can express functions more concisely than existing function expression methods. Arrow functions are always anonymous and do not bind their this, arguments, super and new.target. So it cannot be used as a constructor.
-Effect of arrow function introduction: short function, upper scope this

### short function

```
js
var materials = [
  'Hydrogen',
  'Helium',
  'Lithium',
  'Beryllium'
];

materials.map(function(material) {
  return material.length;
}); // [8, 6, 7, 9]

materials.map((material) => {
  return material.length;
}); // [8, 6, 7, 9]

materials.map(({length}) => length); // [8, 6, 7, 9]
```

After omitting the existing function, replace it with =>

### upper scope this

```
js
function Person(){
  this.age = 0;

  setInterval(() => {
    this.age++; // |this| refers to the person object
  }, 1000);
}

var p = new Person();
```

In general functions, this defines itself as this. However, the arrow function this has the same value as Person's this. This passed to setInterval points to this of Person, and accesses the age of Person object.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#JavaScript)

_JavaScript.end_
