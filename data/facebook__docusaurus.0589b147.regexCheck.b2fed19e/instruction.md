# Bug Report

### Describe the bug

I'm experiencing an issue with whitespace detection in the remark-directive parser. It appears that valid whitespace characters are not being recognized correctly, which causes parsing to fail for directives that should be valid.

### Reproduction

```js
// When parsing markdown with directives that have whitespace
const markdown = `
:::note
This is a note with proper spacing
:::
`;

// The parser fails to recognize the whitespace correctly
// and the directive is not parsed as expected
```

The issue seems to affect any directive that relies on whitespace detection during parsing. The parser is rejecting valid whitespace characters that should be accepted.

### Expected behavior

Whitespace characters (spaces, tabs, newlines, etc.) should be properly detected and the directive should parse correctly. The regex-based whitespace check should return true for valid whitespace character codes.

### System Info
- remark-directive version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
