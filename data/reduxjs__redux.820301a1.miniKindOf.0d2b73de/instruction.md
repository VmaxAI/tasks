# Bug Report

### Describe the bug

I'm experiencing an issue with the `kindOf` utility function where it's not correctly identifying `undefined` values. When I pass `undefined` to the function, it returns the wrong type string.

### Reproduction

```js
import { miniKindOf } from './utils/kindOf'

console.log(miniKindOf(undefined))
// Expected: 'undefined'
// Actual: something else

console.log(miniKindOf(null))
// This works fine: 'null'
```

### Expected behavior

When passing `undefined` to `miniKindOf`, it should return the string `'undefined'`. Currently it's not detecting undefined values properly and falling through to other type checking logic.

### Additional context

This seems to have broken recently. The function works correctly for `null` values but not for `undefined`. This is causing issues in my application where I need to distinguish between undefined and other types.

---
Repository: /testbed
