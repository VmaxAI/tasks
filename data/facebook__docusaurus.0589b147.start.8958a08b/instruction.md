# Bug Report

### Describe the bug

I'm experiencing an issue with inline code parsing in markdown. When I try to use backticks for inline code, the parser seems to be breaking or not recognizing the code text properly.

### Reproduction

```js
const markdown = 'This is `inline code` in text';
const result = parse(markdown);
// The codeText node structure appears incorrect
```

When parsing markdown with inline code (backticks), the resulting AST doesn't seem to be structured correctly. The code text tokens are being created in the wrong order or with incorrect parameters.

### Expected behavior

Inline code wrapped in backticks should be parsed correctly and produce a valid codeText node in the AST. The parser should properly handle the opening backtick sequence and create the appropriate token structure.

### System Info
- remark version: 15.0.1
- Node version: 18.x

---
Repository: /testbed
