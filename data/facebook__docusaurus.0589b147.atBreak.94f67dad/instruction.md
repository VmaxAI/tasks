# Bug Report

### Describe the bug

I'm experiencing an issue with ATX heading parsing where whitespace handling appears to be broken. When there's whitespace after the heading hashes, the parser doesn't properly handle it and seems to be calling the wrong function or skipping necessary processing steps.

### Reproduction

```markdown
## Heading with space
```

When parsing ATX headings (markdown headings starting with `#`), the whitespace between the hash symbols and the heading text is not being processed correctly. The parser seems to immediately call `atBreak` again instead of properly handling the space tokens.

### Expected behavior

The parser should properly tokenize whitespace between the hash symbols and the heading text, allowing the heading to be parsed correctly with proper spacing.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
