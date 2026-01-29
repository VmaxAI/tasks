# Bug Report

### Describe the bug

I'm experiencing an issue with footnote definition labels in GFM (GitHub Flavored Markdown) parsing. When parsing markdown with footnote definitions, the label text is not being captured correctly, resulting in empty or missing footnote labels.

### Reproduction

```markdown
Here's a sentence with a footnote[^1].

[^1]: This is the footnote text.
```

When parsing this markdown, the footnote definition label (the "1" part) doesn't get processed properly. The footnote reference works, but the definition label appears to be lost or empty.

### Expected behavior

The footnote definition should correctly capture and preserve the label text so that footnotes can be properly linked and rendered. The label from `[^1]:` should be available for matching with the reference `[^1]`.

### System Info
- remark-gfm version: 4.0.0
- Parser: micromark with GFM extension

---
Repository: /testbed
