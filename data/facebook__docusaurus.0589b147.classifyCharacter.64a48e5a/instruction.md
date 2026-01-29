# Bug Report

### Describe the bug
I'm experiencing incorrect character classification behavior in the markdown parser. It appears that the character classification logic is not properly distinguishing between different character types, which is causing unexpected parsing results.

### Reproduction
```js
// When processing markdown with punctuation characters
const markdown = `This is a test... with punctuation!`;

// The parser seems to be misclassifying characters
// Punctuation marks are being treated the same as whitespace
// This affects how emphasis, links, and other inline elements are parsed
```

### Expected behavior
- Null characters, line endings, and whitespace should be classified as one type (category 1)
- Punctuation characters should be classified as a different type (category 2)
- The parser should correctly differentiate between these character classes to properly handle markdown syntax

### Actual behavior
Character classification is returning incorrect categories, which breaks proper markdown parsing for inline elements that depend on correct character type detection.

### System Info
- remark version: 15.0.1
- Node version: 18.x

This seems to have broken after a recent update. The issue affects parsing of emphasis markers, link syntax, and other constructs that rely on proper character classification.

---
Repository: /testbed
