# Bug Report

### Describe the bug

I'm experiencing an issue with MDX parsing where flow content seems to get stuck in an infinite loop or doesn't properly continue parsing after certain line endings. The parser appears to hang or fail to process subsequent content correctly.

### Reproduction

```mdx
# Heading

Some content here

Another paragraph
```

When parsing MDX documents with multiple paragraphs separated by blank lines, the parser doesn't seem to advance correctly after processing line endings. The content after blank lines either doesn't get parsed or causes the parser to enter an unexpected state.

### Expected behavior

The parser should correctly handle blank lines between flow content blocks and continue parsing the rest of the document. Each paragraph should be processed independently and the parser should properly reset its state between constructs.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: Latest

---
Repository: /testbed
