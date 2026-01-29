# Bug Report

### Describe the bug

I'm experiencing an issue with GFM table parsing where table cells with escape sequences are not being handled correctly. The markdown parser seems to be consuming characters in the wrong order when processing backslash escapes within table cells.

### Reproduction

```markdown
| Column 1 | Column 2 |
|----------|----------|
| test\|data | normal |
```

When parsing this table, the escaped pipe character (`\|`) in the first cell is not being processed correctly. The parser appears to be treating the data differently than expected.

### Expected behavior

The parser should correctly handle escaped characters within table cells. An escaped pipe (`\|`) should be treated as literal text and not as a cell delimiter. The escape sequence processing should work consistently throughout the table cell content.

### Additional context

This seems to affect how the tokenizer processes character sequences in table header and data rows. The issue manifests when backslash escapes are present in cell content.

---
Repository: /testbed
