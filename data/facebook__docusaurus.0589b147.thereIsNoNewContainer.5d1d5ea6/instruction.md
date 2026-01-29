# Bug Report

### Describe the bug

I'm encountering an issue with lazy line detection in markdown parsing. It seems like the parser is incorrectly identifying certain lines as lazy continuation lines when they shouldn't be, or vice versa.

### Reproduction

When parsing markdown with containers (like blockquotes or lists), the lazy line tracking appears to be inverted. For example:

```markdown
> Quote line 1
  This should be a lazy continuation
> Quote line 3
```

The parser is marking lines as lazy/non-lazy incorrectly, which affects how the markdown is processed and rendered.

### Expected behavior

Lines that are actual lazy continuations (indented lines continuing a block without the container marker) should be correctly identified as lazy. Lines that have proper container markers or are not continuations should not be marked as lazy.

The lazy line tracking should accurately reflect whether a line is continuing a container without its marker present.

### System Info
- remark version: 15.0.1

---
Repository: /testbed
