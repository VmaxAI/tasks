# Bug Report

### Describe the bug

I'm experiencing an issue where browserify seems to be deduplicating modules based on content hash, but it's not working correctly when using the `pattern` option with `require()`. When I specify a pattern to filter which files should be required, the deduplication logic still runs even for files that don't match the pattern, causing unexpected behavior.

### Reproduction

```js
const browserify = require('browserify');
const b = browserify();

// Try to require a file with a pattern filter
b.require('./my-module.js', {
  pattern: '*.config.js',
  expose: 'myModule'
});

// The file doesn't match the pattern but the deduplication 
// logic still executes and registers the module
```

The problem is that when a file doesn't match the specified pattern, the function returns early but the module registry and hash tracking structures have already been initialized. This causes issues when later trying to require modules that should be deduplicated.

### Expected behavior

When a pattern is specified and a file doesn't match it, the function should return early without initializing any module registry or hash tracking. The deduplication logic should only run for files that actually match the pattern.

### System Info
- browserify version: latest
- Node.js version: 18.x

---
Repository: /testbed
