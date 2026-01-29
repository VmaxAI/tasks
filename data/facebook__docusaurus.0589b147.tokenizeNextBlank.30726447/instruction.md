# Bug Report

### Describe the bug

I'm experiencing an issue with blank line handling in MDX parsing. It appears that blank lines are being processed incorrectly, causing the parser to fail or behave unexpectedly when encountering certain markdown structures with empty lines.

### Reproduction

When parsing MDX content with blank lines following specific tokens, the parser doesn't handle them correctly:

```mdx
Some content here

Another line after blank line
```

The parser seems to be treating blank lines in an inverted way - it's calling the wrong callback depending on whether a blank line is present or not. This causes the parsing flow to break or produce unexpected results.

### Expected behavior

Blank lines should be properly recognized and the parser should continue processing subsequent content correctly. The tokenizer should call the appropriate success/failure callbacks based on whether a blank line is actually present.

### System Info
- remark-mdx version: 3.0.0

---
Repository: /testbed
