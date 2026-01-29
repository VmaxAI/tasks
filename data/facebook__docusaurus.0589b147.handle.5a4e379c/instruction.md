# Bug Report

### Describe the bug

I'm encountering an issue with MDX node handling where certain nodes are being skipped or not rendered properly. It seems like when processing MDX content, some elements just disappear from the output without any error being thrown.

### Reproduction

```js
const mdxContent = `
# Hello

<CustomComponent />

Some text here
`;

// Process the MDX content
const result = compile(mdxContent);
// CustomComponent or other elements may not appear in the output
```

When compiling MDX documents with custom components or certain node types, the resulting output is incomplete. Elements that should be present are missing, but there's no error or warning to indicate what went wrong.

### Expected behavior

All nodes in the MDX document should be processed and included in the output. If a node cannot be handled, it should either throw an error or include a fallback representation.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

This seems to have started happening recently. The MDX content compiles without errors, but the output is missing elements that were previously rendering correctly.

---
Repository: /testbed
