# Bug Report

### Describe the bug

I'm experiencing an issue with footnote linking in blog posts. When I have footnotes in my markdown content, the footnote references in the text don't properly link to their corresponding definitions at the bottom of the page.

### Reproduction

Create a blog post with footnotes:

```markdown
---
title: Test Post
---

This is some text with a footnote reference[^1].

Here's another reference[^2].

[^1]: First footnote definition
[^2]: Second footnote definition
```

When the page renders, clicking on the footnote reference (the superscript number) doesn't jump to the correct footnote definition. The links appear to be broken or mismatched.

### Expected behavior

Clicking on a footnote reference should scroll to and highlight the corresponding footnote definition at the bottom of the page. The reference and definition IDs should match so the anchor links work correctly.

### System Info

- Docusaurus version: Latest
- Plugin: @docusaurus/plugin-content-blog

---
Repository: /testbed
