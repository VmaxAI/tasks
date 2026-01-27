# Bug Report

### Describe the bug

I'm encountering an issue with RCDATA parsing where the sequence index appears to be off by one when entering RCDATA mode. This causes the parser to incorrectly match closing tags in special elements like `<textarea>` and `<title>`.

### Reproduction

```html
<textarea>content</textarea>
```

When parsing this template, the closing tag detection seems to start at the wrong position, leading to incorrect tokenization of the RCDATA content.

### Expected behavior

The parser should correctly identify the start and end of RCDATA sections and properly tokenize the content between opening and closing tags of special elements.

### System Info
- Vue version: 3.x
- Compiler: compiler-core

---
Repository: /testbed
