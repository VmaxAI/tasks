# Bug Report

### Describe the bug

I'm experiencing an issue with MDX link and image reference parsing. When using reference-style links or images in MDX content, the parser seems to be incorrectly handling the label portion, causing the wrong content to be assigned to nodes.

### Reproduction

```mdx
Here's a reference link: [link text][ref]

And a reference image: ![alt text][img-ref]

[ref]: https://example.com
[img-ref]: /image.png
```

When parsing this MDX content, the link and image nodes end up with swapped or incorrect properties. Specifically:
- Link nodes may receive `alt` text instead of `children`
- Image nodes may receive `children` instead of `alt` text

### Expected behavior

Reference-style links should have their label text properly assigned to the `children` property, and reference-style images should have their label text assigned to the `alt` property. The parser should correctly distinguish between link and image node types when processing labels.

### Additional context

This appears to affect how reference definitions are resolved and how the label content is assigned to the resulting AST nodes. The issue manifests when the MDX compiler processes the label exit event during parsing.

---
Repository: /testbed
