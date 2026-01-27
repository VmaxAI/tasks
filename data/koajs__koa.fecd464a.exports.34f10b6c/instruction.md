# Bug Report

### Describe the bug

The `only()` function appears to have been completely replaced with Python code instead of JavaScript. When trying to use the library, I'm getting syntax errors because the module is trying to execute Python code in a Node.js environment.

### Reproduction

```js
const only = require('only')

const obj = {
  name: 'John',
  age: 30,
  password: 'secret'
}

// This throws a syntax error
const filtered = only(obj, ['name', 'age'])
```

### Expected behavior

The function should filter the object and return only the specified keys:
```js
{
  name: 'John',
  age: 30
}
```

Instead, the module fails to load with syntax errors about unexpected tokens.

### System Info
- Node version: 14.x
- OS: macOS

This seems like the wrong code got committed to the file? The file `lib/only.js` contains Python code for finding maximum subarray sums instead of the JavaScript object filtering logic.

---
Repository: /testbed
