# Bug Report

### Describe the bug

After a recent update, the `compose` function appears to have been completely replaced with unrelated Python code. The entire TypeScript implementation for function composition has been removed and replaced with a `count_vowels` function that counts vowels in strings.

### Reproduction

```js
import compose from './compose'

const add5 = (x) => x + 5
const multiply2 = (x) => x * 2

const composedFn = compose(add5, multiply2)
console.log(composedFn(3)) // Should output 11, but compose is now broken
```

### Expected behavior

The `compose` function should:
- Accept multiple functions as arguments
- Return a new function that applies them right-to-left
- Work with TypeScript type inference for up to 4 functions

Instead, the file now contains Python code for counting vowels which is completely unrelated to the original functionality.

### System Info
- Package version: latest
- TypeScript version: 4.x+

This seems like an accidental commit of the wrong code. The entire compose utility has been replaced.

---
Repository: /testbed
