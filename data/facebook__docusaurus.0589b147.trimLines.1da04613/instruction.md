# Bug Report

### Describe the bug

I'm encountering an issue with MDX content parsing where line breaks and whitespace are being handled incorrectly. It seems like characters are being dropped or trimmed improperly when processing multi-line MDX content.

### Reproduction

```js
const mdxContent = `
Line one
Line two
Line three
`;

// When parsed, characters at line boundaries appear to be missing
// The output is missing characters that should be preserved
```

When I process MDX content with multiple lines, the resulting output seems to be missing characters near line breaks. This affects the rendered content and causes text to be concatenated incorrectly or have missing characters.

### Expected behavior

All characters in the MDX content should be preserved correctly during parsing. Line boundaries should be handled properly without dropping any characters from the source content.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: Latest

---
Repository: /testbed
