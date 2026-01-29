# Bug Report

### Describe the bug

After a recent update, I'm seeing duplicate entries in the browserify bundle output. When the same module is required multiple times through different paths, it appears multiple times in the recorded dependencies instead of being deduplicated.

### Reproduction

```js
const browserify = require('browserify');
const b = browserify();

// Add the same file through different entry points
b.add('./entry1.js');
b.add('./entry2.js');

// Both entry files require the same shared module
// entry1.js: require('./shared.js')
// entry2.js: require('./shared.js')

b.bundle((err, buf) => {
  // The shared.js module appears twice in the output
  // instead of being deduplicated
});
```

### Expected behavior

Modules that are required multiple times should only appear once in the bundle. The recorder should deduplicate entries based on their file path or module ID before pushing them to the stream.

### Additional context

This seems to have started happening recently. The bundle size has increased significantly because common dependencies are being included multiple times. Not sure if this is related to the recorder implementation or if there's a configuration option I'm missing.

---
Repository: /testbed
