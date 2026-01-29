# Bug Report

### Describe the bug

I'm experiencing an issue with MDX parsing where text content is being incorrectly handled. It seems like the parser is now treating regular text as non-text and vice versa, causing content to not render properly or appear in unexpected places.

### Reproduction

```mdx
# Hello World

This is some regular text content.

More text here.
```

When parsing the above MDX content, the text portions are not being processed correctly. The behavior seems inverted - what should be recognized as text is being treated as something else, and what shouldn't be text is being processed as text.

### Expected behavior

Regular text content in MDX files should be parsed and rendered normally. The parser should correctly identify text segments and handle them appropriately.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

This appears to have started recently, as the same MDX files were working fine before. The logic for determining what constitutes text vs non-text seems to have been inverted somehow.

---
Repository: /testbed
