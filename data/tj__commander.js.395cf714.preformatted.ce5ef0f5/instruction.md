# Bug Report

### Describe the bug

I'm experiencing an issue with text formatting detection in the help system. It seems like the preformatted text detection is not working as expected - text that should be treated as preformatted is being wrapped/reformatted incorrectly.

### Reproduction

When I have help text with indented content like this:

```js
const helpText = `Some description text
  indented code block
  more indented lines`;
```

The indented portions are not being recognized as preformatted text and get reformatted, which breaks the intended formatting.

### Expected behavior

Text containing newlines followed by whitespace/indentation should be detected as preformatted and preserved as-is without wrapping or reformatting. This is important for code examples and other formatted content in help messages.

### System Info
- Node version: 18.x
- OS: macOS

---
Repository: /testbed
