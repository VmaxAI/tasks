# Bug Report

### Describe the bug

The blog post truncation is not working as expected. When using the truncate marker (`<!--truncate-->`), the truncated content includes extra whitespace and the marker itself appears to be processed incorrectly.

### Reproduction

Create a blog post with the following content:

```md
---
title: Test Post
---

This is the intro paragraph that should appear in the list view.

<!--truncate-->

This is the rest of the content that should only appear on the full post page.
```

The truncated content that appears in the blog list view includes unexpected whitespace or doesn't truncate at the correct position.

### Expected behavior

The content before `<!--truncate-->` should be cleanly extracted without extra whitespace, and everything after the marker should be excluded from the preview/list view.

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
