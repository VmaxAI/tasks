# Bug Report

### Describe the bug

Strikethrough formatting in markdown is not being parsed correctly. When using double tildes (`~~`) to create strikethrough text, the parser seems to reject valid strikethrough syntax.

### Reproduction

```markdown
This is ~~strikethrough~~ text.
```

The strikethrough markup should be recognized and parsed properly, but it appears to be getting rejected during tokenization.

### Expected behavior

The markdown parser should correctly handle strikethrough text using the `~~text~~` syntax. The text between the double tildes should be marked as strikethrough.

### Additional context

This affects GFM (GitHub Flavored Markdown) strikethrough parsing. The issue appears to be related to how the tokenizer validates the tilde sequences - valid strikethrough patterns are being incorrectly rejected.

---
Repository: /testbed
