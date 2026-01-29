# Bug Report

### Describe the bug

I'm encountering an issue with inline code parsing in markdown. When using backticks for inline code, the parser seems to be incorrectly handling the closing backtick sequence. The code is not being recognized properly and the output is malformed.

### Reproduction

```markdown
This is `inline code` in a sentence.
```

When parsing this markdown, the inline code block doesn't get recognized correctly. It seems like the parser is treating the closing backtick differently than expected.

Also noticed similar issues with:
```markdown
`code with spaces`
```

The spaces inside the backticks seem to cause problems with the tokenization.

### Expected behavior

Inline code blocks wrapped in backticks should be properly parsed and tokenized. The opening and closing backtick sequences should be matched correctly, and the content between them should be treated as code text data.

### System Info
- remark version: 15.0.1
- Node version: Latest

---
Repository: /testbed
