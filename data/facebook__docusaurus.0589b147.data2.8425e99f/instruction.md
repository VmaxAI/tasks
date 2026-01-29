# Bug Report

### Describe the bug

I'm encountering an issue with ATX heading parsing where hash symbols (`#`) inside heading text are not being handled correctly. When a heading contains a `#` character in its content, the parser seems to be treating it unexpectedly, causing the heading text to be truncated or parsed incorrectly.

### Reproduction

```markdown
# Heading with # symbol inside
## Another heading with # in the middle
### Test # heading
```

When parsing these headings, the text after the internal `#` symbol doesn't appear to be processed as expected. The heading content should include the hash symbol as part of the text, but instead it seems to be causing issues with the tokenization.

### Expected behavior

Headings should be able to contain `#` characters within their text content without breaking the parsing. For example:
- `# Heading with # symbol inside` should parse as a level-1 heading with the full text "Heading with # symbol inside"
- `## Test # heading` should parse as a level-2 heading with the full text "Test # heading"

The hash symbols inside the heading text should be treated as regular characters, not as special markdown syntax.

### System Info
- @mdx-js/mdx version: 3.0.0
- Using the micromark tokenizer for ATX headings

---
Repository: /testbed
