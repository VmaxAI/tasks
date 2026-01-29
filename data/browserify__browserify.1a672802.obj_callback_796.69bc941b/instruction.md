# Bug Report

### Describe the bug

After a recent update, the bundling process seems to hang indefinitely when processing dependencies. The build never completes and just sits there consuming CPU without any output or error messages.

### Reproduction

```js
var browserify = require('browserify');
var b = browserify();

b.add('./entry.js');
b.bundle(function (err, buf) {
  // This callback never gets called
  console.log('Bundle complete');
});
```

Where `entry.js` contains:
```js
var dep = require('./dep');
module.exports = dep;
```

### Expected behavior

The bundle should complete normally and the callback should be invoked with the bundled output. Previously this worked fine but now it just hangs.

### Additional context

This happens consistently on my project but I haven't been able to narrow down exactly what triggers it. The process just stops responding during the dependency resolution phase. No errors are thrown, it just freezes.

Has anyone else experienced this? Any ideas what might be causing it?

---
Repository: /testbed
