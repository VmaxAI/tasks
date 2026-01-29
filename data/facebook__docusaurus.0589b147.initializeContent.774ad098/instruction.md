# Bug Report

### Describe the bug

I'm experiencing an issue with MDX content parsing where the token linking and content chunking order seems to be causing problems with the generated output. The text chunks aren't being processed correctly, and I'm seeing unexpected behavior when parsing markdown content with line endings.

### Reproduction

```js
const mdx = `
This is some text content
with multiple lines
and line endings
`

// Parse the MDX content
const result = await compile(mdx)
// The output structure is malformed
```

When parsing MDX files with text content spanning multiple lines, the token relationships and content chunks appear to be in the wrong order. This affects how the content is structured in the final output.

### Expected behavior

The MDX parser should correctly link tokens and process text chunks in the proper sequence, maintaining the correct relationship between previous/next tokens and properly exiting chunks before consuming line ending codes.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
