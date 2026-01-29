# Bug Report

### Describe the bug

I'm experiencing an issue with GFM table parsing where tables are not being recognized correctly. It seems like the parser is rejecting valid table syntax that should be accepted.

### Reproduction

```markdown
| Header 1 | Header 2 |
|----------|----------|
| Cell 1   | Cell 2   |
```

When parsing this markdown, the table is not being recognized as a valid table structure. The delimiter row (the line with dashes) appears to be getting rejected even though it follows the proper GFM table format.

### Expected behavior

The parser should recognize this as a valid GFM table and parse it accordingly. The delimiter row should be accepted when it appears on the line immediately following the header row.

### Additional context

This seems to affect basic table parsing functionality. The table structure follows the GitHub Flavored Markdown specification, so it should be parsed without issues.

---
Repository: /testbed
