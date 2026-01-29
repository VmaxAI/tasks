# Bug Report

### Describe the bug

I'm encountering an issue with inline code parsing in MDX. When using backticks for inline code, spaces immediately after the opening backtick sequence are not being handled correctly. The parser seems to be treating spaces in a way that breaks the expected behavior.

### Reproduction

```markdown
` code with leading space`
```

When parsing inline code that starts with a space character, the tokenizer doesn't properly handle the transition between the opening backtick sequence and the code content. This affects how the code text is processed and can lead to incorrect parsing results.

### Expected behavior

Inline code with leading/trailing spaces should be parsed correctly according to the CommonMark specification. The space handling between the opening backtick sequence and the actual code content should work as expected.

### Additional context

This appears to be related to the `tokenizeCodeText` function in the MDX parser. The issue manifests when processing code text sequences that contain spaces adjacent to the backticks.

---
Repository: /testbed
