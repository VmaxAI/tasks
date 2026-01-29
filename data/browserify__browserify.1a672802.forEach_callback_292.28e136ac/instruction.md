# Bug Report

### Describe the bug

After a recent update, the `exclude()` method seems to be broken. When I try to exclude files from my bundle, I'm getting unexpected behavior where the method doesn't return properly and the exclusion logic doesn't work as expected.

### Reproduction

```js
var browserify = require('browserify');
var b = browserify();

// This doesn't work correctly anymore
b.exclude(['file1.js', 'file2.js']);
b.bundle(function(err, buf) {
  // Files are not excluded as expected
});
```

When calling `exclude()` with an array of files, the bundling process seems to hang or produce incorrect results. It looks like there might be an issue with how the method handles array inputs and returns.

### Expected behavior

The `exclude()` method should properly exclude the specified files from the bundle and return the browserify instance for method chaining.

### System Info
- Node version: 14.x
- Browserify version: latest

---
Repository: /testbed
