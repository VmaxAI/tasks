# Bug Report

### Describe the bug

The `compose` function is applying functions in the wrong order. When composing multiple functions, they're being executed in reverse of what's expected based on standard function composition behavior.

### Reproduction

```js
const add5 = (x) => x + 5
const multiply2 = (x) => x * 2
const subtract3 = (x) => x - 3

const composed = compose(add5, multiply2, subtract3)

// Expected: subtract3(multiply2(add5(10))) = ((10 + 5) * 2) - 3 = 27
// Actual: add5(multiply2(subtract3(10))) = ((10 - 3) * 2) + 5 = 19
console.log(composed(10))
```

### Expected behavior

Function composition should apply functions from right to left (or in the order they appear in the arguments). The rightmost function should be called first with the initial argument, then each subsequent function should receive the result of the previous one.

For `compose(f, g, h)(x)`, the expected execution order is `f(g(h(x)))`.

### Additional context

This affects any code relying on the compose utility where the order of operations matters. The current implementation appears to be executing functions in the opposite direction.

---
Repository: /testbed
