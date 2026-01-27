# Bug Report

### Describe the bug

The `stripColor` function is not properly removing all ANSI color codes from strings. Some color codes are being left in the output, particularly those with empty parameter sequences.

### Reproduction

```js
const stripColor = require('./lib/help').stripColor;

// This doesn't work correctly
const text1 = '\x1b[m\x1b[31mRed Text\x1b[0m';
console.log(stripColor(text1));
// Expected: 'Red Text'
// Actual: '\x1b[mRed Text' (the \x1b[m is not removed)

const text2 = 'Normal \x1b[mtext with reset';
console.log(stripColor(text2));
// Expected: 'Normal text with reset'
// Actual: 'Normal \x1b[mtext with reset'
```

### Expected behavior

All ANSI escape sequences should be stripped from the string, including reset codes like `\x1b[m` (which is equivalent to `\x1b[0m`).

### Additional context

This issue appears when dealing with certain terminal outputs that use the shorthand reset sequence `\x1b[m` instead of the full `\x1b[0m`. Both are valid ANSI codes and should be handled correctly.

---
Repository: /testbed
