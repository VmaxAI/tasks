# Bug Report

### Describe the bug

Footnote references and definitions are not matching up correctly in blog posts. When using markdown footnotes, the reference links point to the wrong definition IDs, causing broken footnote navigation.

### Reproduction

Create a blog post with footnotes:

```markdown
---
title: Test Post
---

This is some text with a footnote[^1].

[^1]: This is the footnote definition.
```

When the page renders, clicking on the footnote reference `[^1]` doesn't navigate to the correct footnote definition. The IDs appear to be mismatched - the reference and definition are getting different hash suffixes applied.

### Expected behavior

Footnote references should link to their corresponding definitions. Both the reference and definition should use the same identifier suffix so that clicking a footnote number navigates to the correct footnote text at the bottom of the page.

### System Info
- Docusaurus version: latest
- Plugin: @docusaurus/plugin-content-blog

---
Repository: /testbed
