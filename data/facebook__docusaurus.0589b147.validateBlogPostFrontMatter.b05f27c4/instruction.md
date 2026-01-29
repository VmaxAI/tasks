# Bug Report

### Describe the bug

I'm experiencing an issue with blog post tags where the first tag is being removed unexpectedly. When I define tags in the front matter of a blog post, the first tag in the array gets stripped out and doesn't appear in the final output.

### Reproduction

```md
---
title: My Blog Post
tags: [javascript, react, webdev]
---

Blog content here...
```

After processing, only `['react', 'webdev']` appear, but `'javascript'` is missing.

### Expected behavior

All tags defined in the front matter should be preserved and displayed. The tags array should remain `['javascript', 'react', 'webdev']` instead of having the first element removed.

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
