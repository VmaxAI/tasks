# Bug Report

### Describe the bug

I'm experiencing an issue with directive containers in remark-directive where the parser doesn't handle empty content correctly. When a directive container has no content after the opening fence, the parsing behavior seems incorrect.

### Reproduction

```markdown
:::note
:::
```

When parsing this directive container with no content between the opening and closing fences, the parser appears to handle the case incorrectly. The issue also occurs with attributes:

```markdown
:::note{.warning}
:::
```

### Expected behavior

Empty directive containers should be parsed correctly and exit properly when encountering `null` or line endings after the opening fence. The parser should recognize when there's no content and handle it gracefully.

### System Info
- remark-directive version: 3.0.0
- Node version: Latest

---
Repository: /testbed
