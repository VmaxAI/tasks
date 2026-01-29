# Bug Report

### Describe the bug

I'm encountering an issue with footnote back-references in MDX documents. When a footnote is referenced multiple times in the document, the last back-reference link is missing from the footnote's footer section.

### Reproduction

```mdx
Here is some text with a footnote[^1] and another reference to the same footnote[^1] and one more[^1].

[^1]: This is the footnote content.
```

When rendering this document, the footnote footer should contain three back-reference links (one for each usage), but only two are being generated.

### Expected behavior

All footnote references should have corresponding back-reference links in the footnote footer. If a footnote is referenced 3 times in the document, there should be 3 back-reference links in the footer allowing users to jump back to each location where the footnote was used.

### Additional context

This appears to affect the footnote rendering logic. The back-references array seems to be missing the final reference when there are multiple citations of the same footnote.

---
Repository: /testbed
