# Bug Report

### Describe the bug

I'm encountering an issue with inline code parsing in MDX. When using backticks for inline code, the parser seems to be handling spaces incorrectly, which causes the code text to not be properly recognized or tokenized.

### Reproduction

```mdx
This is some text with `inline code` in it.
```

When the above MDX is parsed, the inline code block doesn't get processed correctly. The issue appears to be related to how spaces are handled within the code text sequence.

### Expected behavior

The inline code should be properly tokenized and the backtick-enclosed text should be recognized as code. The parser should correctly handle spaces that appear after the opening backtick sequence.

### Additional context

This seems to affect the tokenization flow in the code text parser. The sequence of operations when encountering spaces and backticks doesn't seem to be working as expected, leading to incorrect parsing results.

---
Repository: /testbed
