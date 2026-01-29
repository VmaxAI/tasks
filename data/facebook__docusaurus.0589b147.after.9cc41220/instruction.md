# Bug Report

### Describe the bug

I'm experiencing an issue with link parsing in markdown where links followed by a caret character (`^`) are not being processed correctly. The parser seems to be rejecting valid link syntax when a `^` appears immediately after the closing bracket.

### Reproduction

```markdown
[example link](https://example.com)^
```

When parsing the above markdown, the link is not recognized properly. The caret character after the link seems to interfere with the link tokenization.

### Expected behavior

The link should be parsed correctly regardless of what character follows it. The `^` character appearing after a link should not affect the link parsing itself - the link should be recognized as valid and the caret should be treated as a separate text node.

### Additional context

This appears to be related to the footnote support logic in the parser. The behavior seems inconsistent - sometimes links are parsed correctly, other times they're rejected based on what follows them.

---
Repository: /testbed
