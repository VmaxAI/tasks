# Bug Report

### Describe the bug

I'm experiencing an issue with markdown parsing where text content is not being processed correctly. It seems like the parser is getting stuck in an infinite loop or not properly recognizing data boundaries when processing text nodes.

### Reproduction

When trying to parse markdown content with regular text, the parser doesn't seem to exit the data state properly. Here's what I'm seeing:

```js
// Simple markdown text
const markdown = `
Hello world

This is a paragraph
`;

// Parser gets stuck or produces incorrect output
const result = remark.parse(markdown);
```

The text content either doesn't get parsed at all or the parser hangs indefinitely.

### Expected behavior

The parser should correctly identify and process text data, properly entering and exiting the "data" state as it encounters text characters and break points. Regular markdown text should be parsed without issues.

### System Info
- remark version: 15.0.1
- Node version: 18.x

---
Repository: /testbed
