# Bug Report

### Describe the bug

I'm experiencing an issue with markdown parsing where whitespace handling seems to be inverted. When processing markdown content, spaces and whitespace characters are being treated incorrectly, causing the parser to fail or produce unexpected output.

### Reproduction

```js
const markdown = `
# Title

Some text with spaces
`;

// Parser fails to correctly handle the whitespace
const result = parse(markdown);
```

When parsing markdown with normal spaces and line breaks, the parser doesn't process them correctly. It seems like the whitespace detection logic is backwards - non-space characters are being treated as spaces and actual spaces are being rejected.

### Expected behavior

The parser should correctly identify and handle whitespace characters (spaces, tabs, newlines) and process the markdown content normally. Regular text with spaces should parse without issues.

### System Info
- remark version: 15.0.1
- Node version: Latest

This is blocking our markdown rendering functionality. Any help would be appreciated!

---
Repository: /testbed
