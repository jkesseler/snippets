# `var` vs. `let` vs. `const`

## `var` is function-level scoped
```javascript
const aFunction = () => {
  var i = 22;

  for (var i = 0; i < 10; i++) {
    console.log(i); // 0, 1, 2, 3, ...
  }
  console.log(i); // 10
}
aFunction();
```

## `let` is block-level scoped
A variable declared with `let` is hoisted to the nearest block scope
```javascript
const aFunction = () => {
  let i = 22;

  for (let i = 0; i < 10; i++) {
    console.log(i); // 0, 1, 2, 3, ...
  }
  console.log(i); // 22MP
}
aFunction();
```

## `const`
With `const` a variable is declared that cannot be re-assigned. There for it must be immediately assigned.
```javascript
const myObj = {};
const myObj = []; // SyntaxError: Identifier 'myObj' has already been declared
```

However `const` is not immutable
```javascript
const myObj = {}:
myObj.someProperty = '123';
console.log(myObj.someProperty); // 123
```

If you want to make a `const` value immutable you can do so yourself with `Object.freeze()`.
```javascript
const myObj = Object.freeze({});
myObj.someProperty = '123'; // TypeError
```
At the time of writing `Object.freeze()` is not supported by any of the major browsers.


## Temporal Dead Zone
Take the follwoing code:
```javascript
console.log(myVar); // undefined
console.log(myLet); // ReferenceError: myLet is not defined
var myVar = 'A var';
let myLet = 'A let';
```
It looks like the `let` declaration is not hoisted because it does not exist yet. While in fact it is hoisted. There is a period between entering scope
where they cannot be accessed and being declared. This period is called the
"Temporal Dead Zone"
