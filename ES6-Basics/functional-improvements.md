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
const obj = {
    foo() {
        ···
    },
    bar() {
        this.foo();
    },
}
```
