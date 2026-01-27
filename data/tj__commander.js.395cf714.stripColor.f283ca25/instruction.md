# Bug Report

### Describe the bug

The `stripColor` function is not removing ANSI color codes correctly. Simple color codes (like `\x1b[0m` for reset or `\x1b[31m` for red) are not being stripped from strings, leaving escape sequences visible in the output.

### Reproduction

```js
const Help = require('./lib/help.js');

// Simple ANSI color codes are not stripped
const coloredText = '\x1b[31mRed text\x1b[0m';
const result = stripColor(coloredText);

console.log('Result:', result);
// Expected: 'Red text'
// Actual: '\x1b[31mRed text\x1b[0m' (color codes still present)
```

### Expected behavior

All ANSI escape sequences should be removed from the string, including basic color codes like `\x1b[0m`, `\x1b[31m`, `\x1b[32m`, etc.

### Additional context

This affects the help output when ANSI colors are used. The escape sequences are showing up in plain text contexts where they shouldn't be visible.

---
Repository: /testbed
