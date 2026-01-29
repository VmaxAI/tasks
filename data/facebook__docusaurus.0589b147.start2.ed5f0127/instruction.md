# Bug Report

### Describe the bug

I'm experiencing an issue with MDX parsing where line breaks in text content are being handled incorrectly. It seems like the parser is treating break characters in the opposite way than it should - when there's a line break, it's being processed as regular text, and when there's regular text, it's being treated as a break.

### Reproduction

```mdx
# Test Document

This is a paragraph with
a line break in the middle.

This should be continuous text.
```

When parsing the above MDX content, the line breaks and text flow are not being processed correctly. The parser appears to be inverting the logic for detecting break characters vs regular text content.

### Expected behavior

Line breaks should be recognized as breaks and handled appropriately by the break construct, while regular text should flow through the text construct. Currently it seems like these are being swapped, causing text to be incorrectly parsed.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: Latest

---
Repository: /testbed
