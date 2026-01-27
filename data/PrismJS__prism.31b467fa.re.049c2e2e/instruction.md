# Bug Report

### Bug in Q# language syntax highlighting

I've noticed that Q# syntax highlighting has completely broken after a recent update. None of the language patterns are being recognized correctly, and code that should be highlighted is showing up as plain text.

### Reproduction

When trying to use Q# code in the editor, patterns that should match keywords, operators, and other language constructs are not working. For example:

```qsharp
operation HelloQ() : Unit {
    Message("Hello quantum world!");
}
```

None of the syntax elements are being highlighted properly. It seems like the regex pattern matching is completely broken.

### Expected behavior

Q# keywords like `operation`, `Unit`, and function names should be properly highlighted according to the language grammar rules.

### Additional context

This appears to affect all Q# code blocks. The issue seems to be related to how regex patterns are being constructed for the language definition, as if the pattern replacement logic isn't working correctly anymore.

---
Repository: /testbed
