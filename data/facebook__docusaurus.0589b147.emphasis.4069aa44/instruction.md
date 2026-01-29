# Bug Report

### Describe the bug

I'm experiencing an issue with emphasis (italic) text rendering in MDX documents. When using emphasis syntax (like `*text*` or `_text_`), the transformed output appears to be incorrectly processing the node children, resulting in either missing content or malformed HTML elements.

### Reproduction

```mdx
This is *emphasized text* in a document.

Here's another _example with emphasis_.
```

When this MDX is processed, the emphasis elements don't render correctly - the children seem to be missing or the element structure is broken.

### Expected behavior

The emphasis syntax should properly convert to `<em>` tags with all the original text content preserved:

```html
This is <em>emphasized text</em> in a document.

Here's another <em>example with emphasis</em>.
```

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: Latest

This seems to have started happening recently. The emphasis handler appears to be processing nodes incorrectly during the transformation phase.

---
Repository: /testbed
