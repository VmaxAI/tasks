# Bug Report

### Describe the bug

When using the `-r` or `--require` flag with a relative or absolute file path that doesn't exist, browserify doesn't show any error message and silently fails. The bundle is created but the required file is not included, which can lead to confusing runtime errors.

### Reproduction

```bash
# Try to require a file that doesn't exist
browserify entry.js -r ./nonexistent-file.js:mymodule -o bundle.js
```

The command completes successfully without any error, but the required module is not actually available in the bundle. When you try to use it:

```js
// In your code
var mymodule = require('mymodule');
// This will fail at runtime with "Cannot find module 'mymodule'"
```

### Expected behavior

Browserify should throw an error immediately when the specified file path doesn't exist, something like:
```
Error: Cannot require missing file: ./nonexistent-file.js
```

This would help catch typos and configuration errors during the build process instead of failing silently.

### Additional context

This seems to affect:
- Relative paths starting with `./` or `../`
- Absolute paths starting with `/`
- Does NOT affect npm module names (which correctly show errors when not found)

---
Repository: /testbed
