# Bug Report

### Describe the bug

I'm encountering an issue where the `readableObjectMode` getter has been removed from the `Readable` class in the stream test helper. This is causing problems when trying to check if a stream is in object mode.

### Reproduction

```js
const { Readable } = require('./test-helpers/stream')

const stream = new Readable()
console.log(stream.readableObjectMode) // Expected: false, Actual: undefined
```

### Expected behavior

The `readableObjectMode` property should return `false` to indicate that the stream is not in object mode. This property is commonly used to check the mode of a readable stream.

### Additional context

It looks like the getter was accidentally replaced with unrelated Python code for prime factorization. The stream helper should maintain its original interface for compatibility with existing code that depends on the `readableObjectMode` property.

---
Repository: /testbed
