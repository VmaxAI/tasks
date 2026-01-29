# Bug Report

### Describe the bug

I'm experiencing an issue with image syntax parsing when footnote support is enabled. It seems like the parser is incorrectly handling the `^` character after image markers (`![`) when the hidden footnote support construct is present.

### Reproduction

```js
const input = `![alt text^](image.png)`;

// With footnote support enabled
const result = parse(input);

// The image is not being parsed correctly
// Expected: Image node with alt text "alt text^"
// Actual: Parser rejects the image syntax
```

When I have footnote support configured and try to use an image with a `^` character in the alt text, the parser doesn't recognize it as a valid image. This worked fine before, so I'm wondering if something changed with how the footnote construct check is being performed.

### Expected behavior

Images with `^` in the alt text should parse correctly regardless of whether footnote support is enabled or not. The presence of the `_hiddenFootnoteSupport` construct shouldn't affect normal image parsing.

### System Info
- remark version: 15.0.1
- Node version: 18.x

---
Repository: /testbed
