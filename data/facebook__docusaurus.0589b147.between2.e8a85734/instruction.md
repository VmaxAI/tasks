# Bug Report

### Describe the bug

I'm encountering an issue with inline code parsing in markdown. When I have inline code with spaces, the parser seems to be handling the token exits incorrectly, which leads to malformed AST output or parsing errors.

### Reproduction

```js
const markdown = '`code with spaces`'
// Parser produces incorrect token structure
```

Also happens with:
```js
const markdown = 'text `inline code` more text'
```

The issue appears to be related to how spaces are handled within backtick-delimited code spans. The parser seems to be exiting tokens at the wrong points.

### Expected behavior

Inline code blocks with spaces should be parsed correctly and produce a valid AST with properly matched enter/exit token pairs.

### System Info
- remark version: 15.0.1
- Node version: 18.x

---
Repository: /testbed
