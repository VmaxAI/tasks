# Bug Report

### Describe the bug

I'm getting a JavaScript error when trying to use array methods on reactive arrays. Specifically, operations like `splice`, `slice`, and other methods that work with array indices are throwing errors about `normalizeSliceIndex` not being defined.

### Reproduction

```js
const state = reactive({
  items: [1, 2, 3, 4, 5]
})

// This throws an error
const sliced = state.items.slice(1, 3)

// This also fails
state.items.splice(2, 1)
```

The error message says something like `normalizeSliceIndex is not a function` or similar.

### Expected behavior

Array methods should work normally on reactive arrays without throwing errors. The `slice` and `splice` operations should execute successfully and return/modify the array as expected.

### System Info
- Version: Latest from main branch
- Environment: Node.js

This seems to have broken recently - it was working fine before. Not sure what changed but it's blocking my work right now.

---
Repository: /testbed
