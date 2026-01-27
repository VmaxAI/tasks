# Bug Report

### Describe the bug

The help text wrapping is not working correctly when the text width exactly matches the specified wrap width. Words that should fit on the current line are being pushed to the next line prematurely.

### Reproduction

```js
const help = new Help();
help.minWidthToWrap = 10;

// When wrapping text at exactly the width boundary
const text = "word1 word2 word3";
const wrapped = help.boxWrap(text, 12);

// Expected: "word1 word2\nword3"
// Actual: "word1 word2" gets split incorrectly
```

When the accumulated width of text chunks equals the target width exactly, the text should still fit on the same line. Currently it seems like text is being wrapped one character too early.

### Expected behavior

Text should wrap to a new line only when it would exceed the specified width, not when it equals the width. If I specify a width of 20 characters, text that is exactly 20 characters wide should fit on one line.

### System Info
- Node version: 18.x
- OS: macOS

---
Repository: /testbed
