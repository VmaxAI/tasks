# Bug Report

### Describe the bug

The `readingTime` function in the blog plugin is returning the wrong value. When I have blog posts with content, the reading time calculation is completely broken - it's just returning the content string itself instead of calculating the actual reading time.

### Reproduction

```js
// In docusaurus.config.js
module.exports = {
  plugins: [
    [
      '@docusaurus/plugin-content-blog',
      {
        // Using default readingTime option
      },
    ],
  ],
};
```

Create a blog post with some content:

```md
---
title: Test Post
---

This is my blog post content with several paragraphs...
```

### Expected behavior

The reading time should be calculated as a number (e.g., "5 min read") based on the content length. Instead, it seems to be returning the raw content string.

### System Info

- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
