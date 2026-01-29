# Bug Report

### Describe the bug

I'm experiencing an issue with footnote back-references in MDX documents. When a footnote is referenced multiple times in the document, the last back-reference link is missing from the footnote section at the bottom of the page.

### Reproduction

```mdx
Here is some text with a footnote[^1].

More text with the same footnote[^1].

And even more text with the same footnote again[^1].

[^1]: This is the footnote text.
```

When rendered, the footnote at the bottom should have three back-reference links (typically shown as ↩︎ symbols) that allow jumping back to each location where the footnote was referenced. However, only two back-reference links appear instead of three.

### Expected behavior

All footnote references should generate corresponding back-reference links in the footnote section. If a footnote is referenced 3 times in the document, there should be 3 back-reference links in the footnote at the bottom.

### Additional context

This seems to affect any footnote that's referenced more than once. The number of back-references is always one less than the actual number of references in the document.

---
Repository: /testbed
