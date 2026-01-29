# Bug Report

### Describe the bug

I'm experiencing an issue with MDX parsing where text content in documents is being incorrectly processed. The content seems to be getting assigned to the wrong nodes in the AST, and position information is also incorrect.

### Reproduction

When parsing an MDX document with text data, the text value ends up in an unexpected location in the syntax tree. For example:

```mdx
Some text content here
```

The text "Some text content here" doesn't appear where it should in the resulting AST structure. Instead, it seems like the value is being added to a parent or sibling node rather than the current node being processed.

Additionally, the position tracking for the end of text nodes appears to be pointing to the start position instead of the actual end position.

### Expected behavior

Text content should be correctly assigned to the appropriate node in the AST, and the position information should accurately reflect the start and end locations of the text in the source document.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

This seems to have started happening recently and is affecting document parsing. Any help would be appreciated!

---
Repository: /testbed
