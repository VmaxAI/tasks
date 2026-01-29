# Bug Report

### Describe the bug

When using the `run()` method with a callback function, the callback is never invoked. The method seems to always use the Promise path instead of properly handling the callback-based API.

### Reproduction

```js
const processor = remark();

processor.run(tree, file, (err, resultTree, file) => {
  // This callback is never called
  console.log('Callback invoked');
  console.log('Result:', resultTree);
});
```

### Expected behavior

When a callback function is provided as the third argument to `run()`, it should be invoked with the transformed tree. The callback-based API should work alongside the Promise-based API.

Currently, even when passing a valid callback function, it's not being executed and the transformation result is lost.

### Additional context

This appears to affect the callback-based usage pattern. The Promise-based API (when no callback is provided) seems to work fine, but the traditional callback pattern is broken.

---
Repository: /testbed
