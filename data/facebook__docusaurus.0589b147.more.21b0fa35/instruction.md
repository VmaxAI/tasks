# Bug Report

### Describe the bug

Strikethrough markdown syntax is not rendering correctly in some cases. When using double tildes (`~~`) to create strikethrough text, the formatting doesn't work as expected and the text remains unformatted.

### Reproduction

```markdown
This ~~should be strikethrough~~ text.
```

When parsing the above markdown, the strikethrough formatting is not being applied properly. The tildes appear to be treated as regular characters instead of formatting markers.

### Expected behavior

The text between `~~` markers should be rendered with strikethrough formatting applied. The parser should correctly identify the opening and closing sequences and apply the appropriate styling.

### System Info
- remark-gfm version: 4.0.0
- Browser: N/A (server-side rendering)

---
Repository: /testbed
