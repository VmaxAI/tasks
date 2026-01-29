# Bug Report

### Describe the bug

I'm experiencing an issue with footnote definitions in GFM (GitHub Flavored Markdown) parsing. It appears that footnote definition containers are not being properly recognized, which is causing problems with nested content inside footnotes.

### Reproduction

```markdown
[^1]: This is a footnote definition
    with multiple lines
    and nested content
```

When parsing the above markdown, the footnote definition doesn't seem to be treated as a proper container. This affects how nested content within the footnote is processed and may cause unexpected behavior with indented content or block-level elements inside footnotes.

### Expected behavior

Footnote definitions should be recognized as container elements that can hold nested content. The parser should properly handle multi-line footnote definitions with indented continuation lines and nested block elements.

### Additional context

This seems to affect how the tokenizer processes footnote definition structures. The container property appears to be set incorrectly, which might be preventing proper nesting behavior.

---
Repository: /testbed
