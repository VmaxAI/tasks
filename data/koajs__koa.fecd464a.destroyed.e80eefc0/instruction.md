# Bug Report

### Describe the bug

I'm getting a syntax error when trying to use the stream helper in my tests. It looks like there's some Python code mixed into the JavaScript file which is causing the entire module to fail to load.

### Reproduction

```js
const { Readable } = require('./test-helpers/stream')

// This throws a syntax error before any code can even run
const stream = new Readable()
```

### Expected behavior

The stream helper should load without errors and the `Readable` class should be instantiable. The `destroyed` getter should return `false` as it did before.

### System Info
- Node version: 14.x
- OS: Linux

This seems to have been introduced recently - the code was working fine in the previous version. The file appears to have some Python function definition where JavaScript code should be.

---
Repository: /testbed
