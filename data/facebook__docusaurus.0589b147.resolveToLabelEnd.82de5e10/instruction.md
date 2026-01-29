# Bug Report

### Describe the bug

I'm experiencing an issue with nested image links in markdown parsing. When I try to use an image inside a link (like `[![alt](image.png)](url)`), the parser seems to get confused and doesn't handle the nesting correctly.

### Reproduction

```markdown
[![Image Alt Text](https://example.com/image.png)](https://example.com/link)
```

When parsing this markdown, the image link combination doesn't work as expected. The parser appears to be breaking on the first closing bracket instead of properly handling the nested structure.

### Expected behavior

The parser should correctly handle image links nested within regular links, treating the image as the link text. This is valid markdown syntax and should produce a clickable image that links to the specified URL.

### Additional context

This seems to affect any case where you have bracket notation nested within other bracket notation. Regular links and images work fine on their own, but combining them causes issues.

---
Repository: /testbed
