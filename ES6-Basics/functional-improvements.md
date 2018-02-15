# Functional improvements
## Arrow functions
Arrow function are syntactically shorter then [function expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/function)
They don't have their own `this`, `arguments`, `super` or `new.target`; They cannot be used as constructors and are bet suited as non-method functions

Basic syntax:
```javascript
(param1, param2) => { statements };
```
If there is only on expression the brackets are optional
```javascript
// These two are the same
(param1, param2) => expression;
(param1, param2) => {return expression};
```

Parentheses are optional if there is only one parameter
```javascript
// These are the same
singleParam => expression;
(singleParam) => { return expression; }
(singleParam) => expression;
```

## `this` and scope
In ES5 `this` referes to the object a method is defined on:
```javascript
var Bear = {
  name: 'Winnie the Pooh',

  sayName: function() {
    console.log(this.name); // Winnie the Pooh
  }
}
```

```javascript
var Bear = {
  name: 'Winnie the Pooh',
  foods: ['honey', 'strawberries'],

  eat: function() {
    this.foods.forEach(function(food) {
      console.log(this.name + ' eats ' + food)
    })
  }
}

Bear.eat();

// [object Window] eats honey
// [object Window] eats strawberries
```
`this` has fallen out of scope and now belongs to the outer object (in this case Window)
That is because in ES5 `this` always references the owner of the function it is in.


In ES6 lambda functions use lexical scoping, `this` refers to it’s current surrounding scope
```javascript
const Bear = {
  name: 'Winnie the Pooh',
  foods: ['honey', 'strawberries'],

  eat() {
    // `this` references the the object
    this.foods.forEach((food) => {
      // `this` references tho the method
      console.log(this.name + ' eats ' + food)
    })
  }
}

Bear.eat();

// Winnie the Pooh eats honey
// Winnie the Pooh eats strawberries
```

## Rest parameters
```javaScript
function (param1, param2, ...theArgs) {

}
```
## default arguments
```javascript
fN(param = x, param2 = y);
fN({a: b, c: d});
```


## Method definitions
```javascript
// in ES5
var obj = {
    foo: function () {
        ···
    },
    bar: function () {
        this.foo();
    }, // trailing comma is legal in ES5
}
```

```javascript
// ES6
const obj = {
    foo() {
        ···
    },
    bar() {
        this.foo();
    },
}
```
