# Bug Report

### Describe the bug

After a recent update, I'm seeing issues with module deduplication in my browserify builds. Some modules that should be deduplicated are being left as-is, and the deduplication seems to be skipping certain files even though they're duplicates.

### Reproduction

```js
var browserify = require('browserify');
var b = browserify();

// Add the same module multiple times
b.add('./mymodule.js');
b.require('./mymodule.js');

b.bundle(function(err, buf) {
  // The output still contains duplicate code
  // even though deduplication should have happened
});
```

I noticed this particularly affects smaller modules. Previously all duplicate modules would be deduplicated regardless of size, but now some are being left alone.

### Expected behavior

All duplicate modules should be deduplicated in the bundle output, resulting in smaller bundle sizes. The deduplication logic should work consistently for modules of any size.

### Additional context

This seems to have started happening recently. My bundle sizes have increased because duplicate code is no longer being properly deduplicated. The behavior changed without any configuration changes on my end.

---
Repository: /testbed
