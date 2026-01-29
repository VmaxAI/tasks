# Bug Report

### Describe the bug

I'm encountering an issue with footnote references in GFM (GitHub Flavored Markdown) parsing. When parsing markdown with footnote calls, the label/identifier is not being captured correctly, resulting in empty or malformed footnote references.

### Reproduction

```markdown
Here is some text with a footnote[^1].

[^1]: This is the footnote content.
```

When parsing this markdown, the footnote reference appears to lose its identifier during the parsing process. The footnote call should capture the label "1" but it seems like the buffer mechanism isn't working as expected.

### Expected behavior

The parser should correctly capture and preserve the footnote identifier/label when processing footnote calls. The footnote reference node should contain the proper identifier that links to the footnote definition.

### Additional context

This seems to affect how footnote references are processed during the AST construction phase. The label extraction mechanism appears to not be functioning correctly.

---
Repository: /testbed
