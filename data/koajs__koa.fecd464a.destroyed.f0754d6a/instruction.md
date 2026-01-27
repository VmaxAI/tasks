# Bug Report

### Describe the bug

I'm experiencing an issue with the `Readable` stream class where accessing the `destroyed` property causes an error. It seems like the property getter has been removed or corrupted somehow.

### Reproduction

```js
const { Readable } = require('./test-helpers/stream')

const stream = new Readable()
console.log(stream.destroyed) // Should return false but throws an error
```

When trying to check if a stream is destroyed, the code fails because the `destroyed` getter is no longer available on the Readable class.

### Expected behavior

The `destroyed` property should return `false` (or the appropriate boolean value indicating whether the stream has been destroyed). This property is commonly used to check the state of streams before performing operations on them.

### Additional context

This appears to have broken after a recent update. The property was working fine before and is needed for stream state management in our application.

---
Repository: /testbed
