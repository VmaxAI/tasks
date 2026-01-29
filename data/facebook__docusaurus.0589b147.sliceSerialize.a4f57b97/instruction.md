# Bug Report

### Describe the bug

I'm encountering an issue with markdown parsing where the serialization of token slices seems to be broken. When processing markdown content, I'm getting errors or unexpected output that suggests the token stream is being sliced incorrectly.

### Reproduction

```js
// Parse markdown content with nested structures
const markdown = `
# Heading
Some text with **bold** and *italic*
`;

const result = processor.parse(markdown);
// Token serialization fails or produces incorrect output
```

### Expected behavior

The markdown should be parsed correctly and tokens should be serialized properly without errors. The sliced token stream should represent the correct portion of the input.

### Additional context

This seems to be related to how token streams are being sliced during the serialization process. The issue appears when processing tokens that need to be serialized with their original content preserved.

---
Repository: /testbed
