# Bug Report

### Describe the bug

The `stripColor` function is not properly removing ANSI color codes from strings. When I pass strings with color escape sequences, some of the codes remain in the output instead of being stripped out completely.

### Reproduction

```js
const coloredString = '\x1b[31mRed text\x1b[0m and \x1b[1;32mBold green\x1b[0m';
const stripped = stripColor(coloredString);

console.log(stripped);
// Expected: "Red text and Bold green"
// Actual: Still contains escape sequences
```

The function should remove all ANSI escape codes but it's leaving some behind. This is causing issues when trying to get the plain text length or when outputting to files.

### Expected behavior

All ANSI color codes should be completely removed from the string, leaving only the visible text content.

### System Info
- Node version: 18.x
- OS: macOS

---
Repository: /testbed
