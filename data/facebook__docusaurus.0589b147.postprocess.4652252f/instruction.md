# Bug Report

### Describe the bug

I'm experiencing an issue with markdown parsing where complex nested structures are not being processed correctly. It seems like the parser is stopping too early when handling certain markdown content with multiple levels of nesting.

### Reproduction

```js
const markdown = `
**Bold text with *nested italic* inside**

[Link with **bold text** inside](https://example.com)

> Quote with **bold** and *italic* text
> > Nested quote with formatting
`;

const result = parse(markdown);
// The nested formatting is incomplete or missing
```

When parsing markdown with multiple layers of nested formatting (like bold text containing italic text, or links with formatted text inside), the output is incomplete. The first level of formatting works fine, but deeper nested elements are not fully processed.

### Expected behavior

All nested formatting should be properly parsed regardless of nesting depth. The parser should continue processing until all nested structures are fully resolved.

### System Info
- remark version: 15.0.1
- Node version: 18.x

---
Repository: /testbed
