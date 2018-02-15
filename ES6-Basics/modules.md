# ES6 Modules

## A simple example
Default named export
```javascript
/* a-module.js */
const aModule = ()=> {
  return 'a String';
}
export default aModule;
```

```javascript
import aModule from './a-module.js';
aModule(); // 'a String';
```

Default unnamed export
```javascript
/* b-module.js */
export default ()=> {
  return 'a String';
}
```

```javascript
import unnamedFn from './b-module.js';
unnamedFn(); // 'a String';
```
