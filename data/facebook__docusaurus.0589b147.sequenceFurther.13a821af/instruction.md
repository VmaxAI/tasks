# Bug Report

### Describe the bug

I'm encountering an issue with parsing ATX-style markdown headings (the ones with `#` symbols). When I have multiple `#` characters at the beginning of a heading, the parser seems to stop processing them correctly after the first one.

### Reproduction

```markdown
## This is a heading
### Another heading
#### Four levels deep
```

When parsing headings with multiple hash symbols, the tokenizer appears to exit the sequence processing too early. This affects how the heading level is determined and can cause the heading structure to be malformed.

### Expected behavior

The parser should correctly process all consecutive `#` characters at the start of a heading line to determine the proper heading level (h1 through h6). Each additional `#` should be consumed as part of the heading sequence before moving on to parse the heading text.

### Additional context

This seems to affect the `tokenizeHeadingAtx` function in the remark parser. The sequence processing logic for consecutive hash characters doesn't appear to be working as intended.

---
Repository: /testbed
