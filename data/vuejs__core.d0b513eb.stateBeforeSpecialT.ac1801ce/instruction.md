# Bug Report

### Describe the bug

I'm encountering an issue with parsing `<textarea>` tags in templates. It seems like the compiler is not correctly recognizing textarea elements and treating them as regular tags instead of special elements.

### Reproduction

```vue
<template>
  <textarea>
    Some content here
  </textarea>
</template>
```

When compiling templates with textarea elements, the parser doesn't handle them properly. The content inside the textarea is not being treated as raw text like it should be.

### Expected behavior

The `<textarea>` tag should be recognized as a special element (similar to `<title>`) and its content should be parsed as raw text, not as potential HTML/template syntax.

### System Info
- Vue version: 3.x
- Node version: 18.x

---
Repository: /testbed
