# Destructuring

Destructuring is a way of extracting values from object and arrays and use them as distinct variables.

```javascript
const person  = { fistName: 'John', lastName: 'Wilkins' };

const { firstName, lastName } = person;
console.log(firstName); // John
console.log(lastName); // Wilkins
```

Also works on arrays
```javascript
const person  = [ 'John', 'Wilkins' ];

const { x, y } = person;
console.log(x); // John
console.log(y); // Wilkins
```

Pick and choose what values to extract:
```javascript
[a, b] = [1, 2, 3, 4, 5];
console.log(a); // 1
console.log(b); // 2
```

Using a rest operator
```javascript
[a, b, ...theRestOfTheValues] = [1, 2, 3, 4, 5];
console.log(a); // 1
console.log(b); // 2
console.log(theRestOfTheValues); // [3, 4, 5]
```



## Destructuring assignment
```javascript
const object = { a: 'value', b: args => ...args , c: { x: 'val', y:'val2' } };
const {a, b, c: { x, y } } = object;
```

## Nested destructuring
```javascript
const App = {
    model: {
        User: function(){ .. }
    }
};

// instead of: var User = App.model.User;
const { model: { User } } = App;
```

```javascript
const a1 = [ 1, [ 2, 3, 4 ], 5 ];
const [ a, [ b, c, d ], e ] = a1;
console.log( a, b, c, d, e );        // 1 2 3 4 5

const o1 = { x: { y: { z: 6 } } };
const { x: { y: { z: w } } } = o1;
console.log( w );                    // 6


```
