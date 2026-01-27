# Bug Report

### Describe the bug

The `false` language syntax highlighting is not correctly handling character codes with newlines. When a character code contains a newline character, it's not being tokenized properly.

### Reproduction

```false
'a    { regular character code - works fine }
'\n   { newline character code - not highlighting correctly }
'\r   { carriage return - also broken }
```

The character-code pattern doesn't seem to recognize newline sequences properly. Only single-line character codes are being highlighted.

### Expected behavior

Character codes like `'\n` and `'\r` should be recognized and highlighted the same way as other character codes like `'a` or `'b`. The pattern should handle newline characters in addition to regular characters.

### System Info
- Language: false
- Affected token type: character-code

---
Repository: /testbed
