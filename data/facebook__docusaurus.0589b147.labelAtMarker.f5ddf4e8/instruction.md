# Bug Report

### Describe the bug

Footnote definitions in GFM (GitHub Flavored Markdown) are not being parsed correctly. When trying to use footnotes with the `[^label]:` syntax, they're not being recognized as valid footnote definitions.

### Reproduction

```markdown
Here's a sentence with a footnote.[^1]

[^1]: This is the footnote definition.
```

When parsing this markdown, the footnote definition `[^1]:` is not being recognized. The parser seems to be rejecting valid footnote syntax.

### Expected behavior

The parser should correctly identify and process footnote definitions that start with `[^` followed by a label and `]:`. The footnote reference and definition should be properly linked.

### System Info
- remark-gfm version: 4.0.0

---
Repository: /testbed
