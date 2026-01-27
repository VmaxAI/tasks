# Bug Report

### Describe the bug

The `preformatted()` method is not correctly detecting preformatted text in help strings. It seems to be checking for the wrong pattern, causing some multi-line strings with indentation to be incorrectly identified as preformatted or non-preformatted.

### Reproduction

```js
const help = new Help();

// This should be detected as preformatted (has newline followed by whitespace)
const text1 = "First line\n  Indented second line";
console.log(help.preformatted(text1)); // Returns unexpected result

// This should NOT be detected as preformatted (whitespace before newline)
const text2 = "First line  \nSecond line";
console.log(help.preformatted(text2)); // Returns unexpected result
```

The logic appears to be reversed or checking the wrong sequence of characters. Strings with newlines followed by whitespace should be treated as preformatted, but the current behavior is inconsistent.

### Expected behavior

The method should return `true` when a string contains a newline character followed by whitespace (indicating indented/preformatted content), and `false` otherwise.

### System Info
- Node version: 18.x
- Library version: latest

---
Repository: /testbed
