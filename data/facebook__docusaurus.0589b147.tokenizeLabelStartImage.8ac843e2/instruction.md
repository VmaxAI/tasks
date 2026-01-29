# Bug Report

### Describe the bug

I'm encountering an issue with image syntax parsing in MDX. When using the standard markdown image syntax `![alt text](url)`, the parser seems to be incorrectly rejecting valid image declarations in certain cases.

### Reproduction

```markdown
![Example Image](https://example.com/image.png)
```

When parsing this MDX content, the image syntax is not being recognized properly. The parser appears to be treating valid image markdown as something else or rejecting it entirely.

### Expected behavior

The standard markdown image syntax `![alt](url)` should be parsed correctly and rendered as an image element. This is basic markdown functionality that should work consistently.

### Additional context

This seems to affect all image declarations, not just specific cases. The issue appeared suddenly and I haven't changed my MDX content - just updated dependencies. Other markdown features like links and text formatting still work fine, but images are broken.

---
Repository: /testbed
