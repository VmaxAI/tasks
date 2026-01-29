# Bug Report

### Describe the bug

I'm experiencing an issue where middleware error handling seems to be broken. When an error occurs in middleware processing, the callback gets invoked multiple times with the same error, causing unexpected behavior in my application.

### Reproduction

```js
const processor = unified()
  .use(function() {
    return function(tree, file, next) {
      // Simulate an error in middleware
      throw new Error('Processing failed');
    };
  });

processor.process('some content', (err, result) => {
  console.log('Callback invoked');
  // This callback is being called multiple times
});
```

### Expected behavior

The error callback should only be invoked once when an error occurs during processing. Currently it appears to be called multiple times, which breaks error handling logic that assumes single invocation.

### Additional context

This seems to affect middleware that uses both synchronous throws and asynchronous error handling. The duplicate callbacks are causing issues in production where we track error metrics and the counts are inflated.

---
Repository: /testbed
