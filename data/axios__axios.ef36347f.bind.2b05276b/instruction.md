# Bug Report

### Describe the bug

I'm experiencing an issue with bound functions where only the first argument is being passed through, and subsequent arguments are being ignored. Additionally, the `thisArg` parameter that should be used for binding seems to be replaced with the current execution context.

### Reproduction

```js
function myFunction(arg1, arg2, arg3) {
  console.log('this:', this);
  console.log('arg1:', arg1);
  console.log('arg2:', arg2);
  console.log('arg3:', arg3);
}

const context = { name: 'myContext' };
const boundFn = bind(myFunction, context);

boundFn('first', 'second', 'third');
// Expected: this should be context, all three args should be passed
// Actual: only 'first' is received, other args are undefined
```

### Expected behavior

When binding a function with `bind()`, all arguments passed to the wrapped function should be forwarded to the original function, and the bound context should be preserved.

### Additional context

This appears to affect any function that expects multiple arguments. The bound function only receives the first argument, making it impossible to use with functions that require multiple parameters.

---
Repository: /testbed
