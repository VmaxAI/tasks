# Bug Report

### Describe the bug

The `compose()` function is not working as expected when composing multiple functions together. The functions seem to be executing in the wrong order, and when no functions are passed, it returns `undefined` instead of the identity function.

### Reproduction

```js
const add5 = (x) => x + 5
const multiply2 = (x) => x * 2
const subtract3 = (x) => x - 3

// Composing multiple functions
const composed = compose(add5, multiply2, subtract3)
const result = composed(10)

// Expected: add5(multiply2(subtract3(10))) = add5(multiply2(7)) = add5(14) = 19
// But getting incorrect result

// Also, empty compose doesn't work:
const identity = compose()
console.log(identity(42)) // Returns undefined instead of 42
```

### Expected behavior

1. When composing functions, they should execute right-to-left (the standard compose behavior)
2. When `compose()` is called with no arguments, it should return an identity function that returns its argument unchanged

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
