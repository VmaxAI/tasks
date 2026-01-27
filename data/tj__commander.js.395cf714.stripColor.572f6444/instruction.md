# Bug Report

### Describe the bug

The `stripColor` function is not removing all ANSI color codes from strings. When a string contains multiple color codes, only the first one gets stripped and the rest remain in the output.

### Reproduction

```js
const stripColor = require('./lib/help').stripColor;

const coloredText = '\x1b[31mRed\x1b[0m and \x1b[32mGreen\x1b[0m';
const result = stripColor(coloredText);

console.log(result);
// Expected: "Red and Green"
// Actual: "Red\x1b[0m and \x1b[32mGreen\x1b[0m"
```

### Expected behavior

All ANSI escape codes should be removed from the string, not just the first occurrence.

### Additional context

This seems to affect any string with multiple color codes. Single colored strings work fine, but anything with more than one escape sequence leaves the subsequent codes in place.

---
Repository: /testbed
