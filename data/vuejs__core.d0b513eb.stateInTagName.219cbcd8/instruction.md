# Bug Report

### Describe the bug

I'm encountering an issue with template parsing where tag names are being processed incorrectly. It seems like the tokenizer is calling `handleTagName()` unconditionally now, even when it shouldn't be processing the tag name yet.

### Reproduction

```vue
<template>
  <div>
    <custom-component />
  </div>
</template>
```

When the compiler tries to parse templates with custom components or standard HTML tags, the tag name handling appears to be triggered prematurely. This causes the parser to process incomplete tag names or process them at the wrong point in the tokenization flow.

### Expected behavior

The tokenizer should only call `handleTagName()` when it reaches the end of a tag section (like whitespace, `>`, or `/>`), not on every character while still reading the tag name.

### System Info
- Vue version: 3.x
- Build tool: Vite

---
Repository: /testbed
