# Bug Report

### Describe the bug

I'm experiencing an issue with inline markdown patterns not being replaced correctly. When using patterns that contain `<inner>` placeholders, they're not being substituted with the actual inner content - instead the literal string `<inner>` remains in the pattern.

### Reproduction

```js
// When processing markdown with nested inline elements like:
**bold text with `code` inside**

// The <inner> placeholder in patterns is not being replaced
// This causes the regex to fail matching nested structures
```

The issue appears to affect any markdown syntax that has nested inline elements - bold text containing code blocks, italic text with links, etc.

### Expected behavior

The `<inner>` placeholder in inline patterns should be replaced with the actual inner pattern content, allowing nested inline markdown elements to be parsed correctly.

### System Info
- Prism version: latest
- Affected language: Markdown

---
Repository: /testbed
