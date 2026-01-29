# Bug Report

### Describe the bug

I'm experiencing an issue with MDX parsing where destructuring errors are not being tracked correctly. It seems like the error tracking state is getting initialized with incorrect values, which causes the parser to fail to detect certain syntax errors in destructuring patterns.

### Reproduction

```js
// This should raise a destructuring error but doesn't
const obj = {
  a: 1,
  a: 2  // duplicate property
}

// Also this pattern with trailing commas behaves unexpectedly
const { x, } = someObject
```

The parser seems to be initializing the error tracking properties in the wrong order or with wrong values, causing it to miss these edge cases.

### Expected behavior

The parser should correctly track and report destructuring errors like:
- Duplicate properties in object literals
- Invalid trailing commas in destructuring patterns
- Other destructuring-related syntax errors

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
