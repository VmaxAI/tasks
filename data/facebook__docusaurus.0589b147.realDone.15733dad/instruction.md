# Bug Report

### Describe the bug

I'm experiencing an issue with the remark processor where transformations are not being applied correctly. When I process markdown content, the output tree is always undefined instead of containing the transformed AST.

### Reproduction

```js
const processor = remark();
const file = await processor.process('# Hello World');

// Expected: file should contain transformed AST
// Actual: resulting tree is undefined
console.log(file); // tree is undefined
```

This seems to happen when using the async `process()` method. The transformation runs but the output is not what I expect.

### Expected behavior

The processor should return the transformed AST tree after running all transformers. The resulting tree should contain the processed markdown structure, not undefined.

### Additional context

This might be related to how the processor handles the transformation callback. The issue appeared recently and I'm not sure if it's a regression or if I'm using the API incorrectly.

---
Repository: /testbed
