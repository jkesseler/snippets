# Not so common language features
[pipeline operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Pipeline_operator)

```javascript
// This is an experimental feature not supported by most common JS runtimes
const add = (n) => n + n;
const multiply = (n) => n * n;
const x  = add(multiply(add(6)); // 288

// With pipeline operator
x |> add |> multiply |> add
```

<!--
Label statements
void Operator
, (comma) operator in ternary operators and return statements

-->
