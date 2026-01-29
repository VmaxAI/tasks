# Bug Report

### Describe the bug

I'm encountering an issue with markdown link parsing where links followed by a caret character (`^`) are not being processed correctly. It seems like the parser is treating these links differently than expected.

### Reproduction

```markdown
[link text](url)^some text
```

When parsing markdown content that has a link immediately followed by a caret symbol, the link is not being recognized or parsed properly. The behavior seems inconsistent with how links should be handled in standard markdown.

### Expected behavior

Links should be parsed correctly regardless of whether they're followed by a `^` character. The caret should be treated as a separate text node after the link, and the link itself should be properly tokenized.

### Additional context

This appears to affect link parsing specifically when the `_hiddenFootnoteSupport` construct is present in the parser configuration. The link token seems to be rejected when it should be accepted, or vice versa.

---
Repository: /testbed
