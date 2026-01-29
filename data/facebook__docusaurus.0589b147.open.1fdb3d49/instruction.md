# Bug Report

### Describe the bug

Image syntax is not being parsed correctly in markdown. When trying to use the standard markdown image syntax `![alt text](url)`, the parser seems to be rejecting valid image references or not recognizing them properly.

### Reproduction

```js
const markdown = '![test image](https://example.com/image.png)'

// Parse the markdown
const result = parse(markdown)

// Expected: Image node to be created
// Actual: Image syntax is not recognized or parsed incorrectly
```

### Expected behavior

The parser should correctly recognize and tokenize the image syntax `![alt](url)` as a valid markdown image element. The opening `![` sequence should be properly identified and the subsequent content should be processed as an image reference.

### System Info
- remark version: 15.0.1

---
Repository: /testbed
