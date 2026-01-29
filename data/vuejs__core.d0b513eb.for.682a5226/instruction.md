# Bug Report

### Describe the bug

I'm encountering an issue with catch clause variable handling in the compiler. When using a catch block with a parameter, the caught error variable is not being properly recognized in the scope, leading to incorrect identifier tracking.

### Reproduction

```js
try {
  throw new Error('test')
} catch (error) {
  // The 'error' identifier is not being tracked correctly
  console.log(error.message)
}
```

Or with destructuring:

```js
try {
  throw new Error('test')
} catch ({ message }) {
  // Destructured catch parameters also affected
  console.log(message)
}
```

### Expected behavior

The catch clause parameter should be properly recognized as a scoped identifier and tracked correctly by the compiler. Variables bound in catch clauses should be available within the catch block without issues.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

---
Repository: /testbed
