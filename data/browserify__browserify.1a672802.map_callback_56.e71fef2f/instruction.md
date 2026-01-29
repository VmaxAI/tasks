# Bug Report

### Describe the bug

After a recent update, browserify seems to have issues with glob patterns in entry points. When I try to use glob patterns like `src/**/*.js` or `lib/*.js` as entry points, they don't get expanded properly and browserify fails to find the files.

### Reproduction

```js
// Command line usage
browserify 'src/**/*.js' -o bundle.js

// Or programmatically
var browserify = require('browserify');
var b = browserify(['lib/*.js']);
b.bundle().pipe(process.stdout);
```

The glob patterns are not being expanded to match the actual files. Instead, browserify tries to treat the pattern as a literal filename and can't find it.

### Expected behavior

Glob patterns in entry points should be expanded to match all files that fit the pattern. For example, `lib/*.js` should match `lib/a.js`, `lib/b.js`, etc., and all matched files should be included as entry points.

### Additional context

This used to work in previous versions. I'm not sure what changed but it seems like glob expansion is no longer happening for entry point arguments.

---
Repository: /testbed
