# Bug Report

### Describe the bug

I'm experiencing an issue with blank line parsing in markdown content. When processing markdown text that contains blank lines with leading spaces, the parser is not handling them correctly. Lines that should be recognized as blank lines are being rejected instead.

### Reproduction

```js
// Markdown content with spaces before a blank line
const markdown = `
First paragraph

  
Second paragraph
`;

// The blank line with spaces is not being recognized properly
// Expected: line should be treated as blank
// Actual: line is rejected and parsing fails
```

### Expected behavior

Blank lines that contain only whitespace characters (spaces, tabs) should be recognized and tokenized as valid blank lines. The parser should accept these lines and continue processing the markdown correctly.

### System Info
- remark version: 15.0.1
- Node version: Latest

This seems to have started recently - blank lines with leading whitespace used to work fine but now they're causing parsing issues. Not sure if this is a regression or if I'm missing something in my setup.

---
Repository: /testbed
