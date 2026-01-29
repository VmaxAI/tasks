# Bug Report

### Describe the bug

I'm encountering an issue with blank line tokenization in MDX content. It seems like the parser is incorrectly handling whitespace characters at the start of blank lines, causing unexpected behavior when processing markdown documents.

### Reproduction

When parsing MDX content with blank lines that contain leading whitespace, the tokenizer doesn't properly recognize them as blank lines. This affects document structure parsing.

```js
const content = `
# Heading

   
Another paragraph
`;

// The blank line with spaces is not being handled correctly
// Expected to be treated as a blank line but it's not
```

### Expected behavior

Blank lines with or without leading whitespace should be consistently recognized as blank lines by the tokenizer. The parser should handle both cases:
- Lines with only whitespace characters
- Completely empty lines

Both should be treated as valid blank lines for markdown structure purposes.

### System Info
- remark-mdx version: 3.0.0
- Node version: Latest

---
Repository: /testbed
