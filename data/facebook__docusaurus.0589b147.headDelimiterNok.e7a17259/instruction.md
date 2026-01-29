# Bug Report

### Describe the bug

I'm encountering an issue with table parsing in markdown. When a table has an invalid header delimiter row, the parser seems to fail silently or behave unexpectedly instead of properly handling the error case.

### Reproduction

```markdown
| Header 1 | Header 2 |
| invalid delimiter row without proper dashes |
| Cell 1 | Cell 2 |
```

When parsing markdown tables with malformed delimiter rows, the error callback doesn't receive the expected code parameter. This causes issues when trying to determine what character caused the parsing to fail or when the callback tries to use that parameter for further processing.

### Expected behavior

The parser should properly pass the character code to the error callback so that error handling can work correctly and provide meaningful feedback about what went wrong during table parsing.

### System Info
- remark-gfm version: 4.0.0
- Node version: Latest

---
Repository: /testbed
