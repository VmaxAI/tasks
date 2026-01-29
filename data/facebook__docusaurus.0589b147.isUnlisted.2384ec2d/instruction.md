# Bug Report

### Describe the bug

I'm encountering an issue with blog tag visibility calculation. When blog posts have the `unlisted` property, the tag visibility is being determined incorrectly. Tags that should be visible are showing as unlisted, and vice versa.

### Reproduction

```js
const blogPost = {
  unlisted: false,
  metadata: {
    unlisted: false
  }
}

// Tag visibility is calculated incorrectly
// Expected: tag should be visible
// Actual: tag is marked as unlisted
```

### Expected behavior

Tag visibility should correctly reflect the unlisted status of blog posts. If a blog post is not unlisted, its tags should be visible.

### Additional context

This seems to affect how tags are displayed in the blog listing pages. The logic for determining whether a tag should be unlisted appears to be inverted or checking the wrong property.

---
Repository: /testbed
