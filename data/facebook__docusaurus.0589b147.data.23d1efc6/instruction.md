# Bug Report

### Describe the bug

I'm encountering an issue with parsing directives that contain backslashes in their labels. When a directive label includes a backslash character (e.g., for escaping), the parser seems to get stuck in an infinite loop or produces unexpected behavior.

### Reproduction

```markdown
:directive[label with \\ backslash]

:another[text with \[ escaped bracket]
```

When parsing markdown with directives that have escaped characters in their labels, the parser doesn't handle them correctly. The backslash escaping logic appears to be inverted - it's treating non-backslash characters as escape sequences instead of the backslash itself.

### Expected behavior

Directives with escaped characters in labels should parse correctly:
- `\[` should be treated as an escaped opening bracket
- `\\` should be treated as an escaped backslash
- The parser should properly toggle between normal data processing and escape handling

### Additional context

This also affects the closing bracket balance check - when there are no opening brackets, the closing bracket counter can go negative which causes issues with detecting when to exit the label parsing.

---
Repository: /testbed
