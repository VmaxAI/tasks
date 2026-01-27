# Bug Report

### Describe the bug

The `compose()` function is not working correctly when chaining multiple functions together. The functions are being applied in the wrong order, which completely breaks function composition.

### Reproduction

```js
const add5 = (x) => x + 5
const multiply2 = (x) => x * 2
const subtract3 = (x) => x - 3

const composed = compose(add5, multiply2, subtract3)

// Expected: subtract3(multiply2(add5(10))) = subtract3(multiply2(15)) = subtract3(30) = 27
// Actual: Getting wrong result
console.log(composed(10))
```

When I compose these functions, the result is incorrect. It seems like the functions are being executed in reverse order or something is wrong with how they're being combined.

Also noticed that when passing a single function to `compose()`, it returns `undefined` instead of the function itself.

```js
const single = compose(add5)
console.log(single(10)) // throws error, single is undefined
```

### Expected behavior

- Functions should be composed right-to-left (the standard mathematical composition order)
- `compose(f, g, h)(x)` should equal `f(g(h(x)))`
- `compose(f)` should return `f` itself

### System Info
- Version: latest
- Node: 18.x

---
Repository: /testbed
