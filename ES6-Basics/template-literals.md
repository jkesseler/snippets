# Tempalte literals

## Before we had string concatenation:
```javascript
const string = 'my only friend';
console.log('this is the end ' + string + ' the end');
```

With template literals the syntax changes a bit
```javascript
console.log(`this is the end ${string} the end`);
```

## We can do multiline strings with ease
```javascript
console.log(`this is
a sentence over
multiple lines`);
```


## Tagged Templates
A tag is that accepts a template literal
```javascript
const place = 'end';
const who = 'friend';
const templateLiteral  = tag`This is the ${place} my only ${who} the end`
```

although the semantics change quite a bit, it 'desugars' into:
```javascript
tag(['this is the', 'my only', 'the end'], place, who);
```
