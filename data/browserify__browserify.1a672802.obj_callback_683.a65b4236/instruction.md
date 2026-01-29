# Bug Report

### Describe the bug

After a recent update, browserify is throwing errors when processing files. It looks like there's a syntax error in the code that's preventing the bundling process from working at all.

### Reproduction

```js
const browserify = require('browserify');
const b = browserify();

b.add('entry.js');
b.bundle(function (err, buf) {
  if (err) {
    console.error(err);
  } else {
    console.log(buf.toString());
  }
});
```

Running this with any entry file causes an error during the bundle process. The error seems to be coming from within browserify itself, not from my code.

### Expected behavior

The bundle should complete successfully without any internal errors from browserify.

### System Info
- Node version: 14.x
- browserify version: latest

This was working fine before the latest update. Any help would be appreciated!

---
Repository: /testbed
