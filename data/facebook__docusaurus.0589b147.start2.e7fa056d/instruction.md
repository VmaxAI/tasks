# Bug Report

### Describe the bug

I'm experiencing an issue with MDX parsing where certain character codes are not being handled correctly. When processing content with specific characters, the parser seems to skip or mishandle constructs that should be triggered.

### Reproduction

```js
// Example MDX content that triggers the issue
const mdxContent = `
# Heading

Some text with special characters or null codes
`;

// Parse the content
const result = compile(mdxContent);
```

The parser doesn't properly match constructs when it encounters certain character codes. It appears that the logic for checking character mappings is not working as expected, causing some valid MDX syntax to be ignored or parsed incorrectly.

### Expected behavior

The parser should correctly identify and process all valid constructs based on the character code mappings, including handling null character scenarios properly.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
