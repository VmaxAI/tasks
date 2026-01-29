# Bug Report

### Describe the bug

After a recent update, I'm experiencing an issue where calling `require()` multiple times on the same file causes the bundler to skip subsequent requires. The file is only included once in the bundle even when it should be required with different IDs or options.

### Reproduction

```js
const browserify = require('browserify');
const b = browserify();

// First require
b.require('./mymodule.js', { expose: 'module1' });

// Second require with different expose - this gets ignored
b.require('./mymodule.js', { expose: 'module2' });

b.bundle((err, buf) => {
  // Only 'module1' is available, 'module2' is missing
  console.log(buf.toString());
});
```

The second `require()` call doesn't add the file to the bundle. It seems like there's some internal tracking that's preventing the same file from being required multiple times, even when using different expose names or aliases.

### Expected behavior

Each `require()` call should be processed independently. If I require the same file with different expose names, both should be available in the final bundle. The file should be included multiple times if needed (or at least aliased properly).

### System Info
- Node version: 18.x
- OS: Windows 10

This is blocking our build process where we need to expose the same module under different names for compatibility reasons. Any help would be appreciated!

---
Repository: /testbed
