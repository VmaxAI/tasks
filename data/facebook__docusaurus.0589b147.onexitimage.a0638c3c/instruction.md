# Bug Report

### Describe the bug

Images in MDX are not being processed correctly - it looks like reference-style images and inline images are getting their properties swapped. When I use an inline image with a URL, it's being treated as a reference, and reference-style images are being treated as inline.

### Reproduction

```mdx
<!-- Inline image - should have url property -->
![alt text](https://example.com/image.png "title")

<!-- Reference-style image - should have identifier/label -->
![alt text][ref]

[ref]: https://example.com/image.png "title"
```

After processing, the inline image is missing its `url` and `title` properties (they're being deleted) and instead has `identifier` and `label` properties. The reference-style image has the opposite problem - it has `url` and `title` when it should have `identifier` and `label`.

### Expected behavior

- Inline images should preserve their `url` and `title` properties
- Reference-style images should preserve their `identifier` and `label` properties  
- The `type` property should only have "Reference" appended for actual reference-style images

### System Info

- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
