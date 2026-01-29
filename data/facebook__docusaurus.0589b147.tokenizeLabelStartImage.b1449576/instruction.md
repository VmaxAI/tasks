# Bug Report

### Describe the bug

Image syntax in markdown is not being parsed correctly. When trying to use the standard markdown image syntax `![alt text](url)`, it's not being recognized as an image element.

### Reproduction

```markdown
![Example Image](https://example.com/image.png)
```

When parsing this markdown, the image syntax is not being tokenized properly. The opening bracket sequence `![` should be recognized as the start of an image, but it appears the tokenizer is checking for the wrong character code.

### Expected behavior

The markdown parser should correctly recognize `![...]` as image syntax and parse it into the appropriate image element. The standard markdown image syntax should work as documented.

### Additional context

This seems to affect all image references in markdown documents. Regular links with `[text](url)` might still work, but the image variant with the exclamation mark prefix is broken.

---
Repository: /testbed
