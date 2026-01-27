# Bug Report

### Describe the bug

The `readable` property on stream objects is no longer accessible. When trying to check if a stream is readable, the property returns `undefined` instead of the expected boolean value.

### Reproduction

```js
const stream = new Readable()

// This returns undefined instead of true
console.log(stream.readable)
```

### Expected behavior

The `readable` property should return `true` for readable stream instances. This is used to check whether a stream is in a readable state before attempting to read from it.

### Additional context

This appears to have broken after a recent change. Code that was previously working and checking `stream.readable` before performing operations is now failing because the property is undefined.

---
Repository: /testbed
