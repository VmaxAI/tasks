# Bug Report

### Describe the bug

I'm encountering an issue with the template compiler where `<textarea>` tags are not being parsed correctly. When I have a textarea element in my template, it seems like the parser is not properly recognizing the closing tag, which causes the content after the textarea to be treated incorrectly.

### Reproduction

```vue
<template>
  <div>
    <textarea>Some content</textarea>
    <p>This paragraph should be outside the textarea</p>
  </div>
</template>
```

When compiling this template, the parser doesn't properly handle the textarea element. The content that should appear after the closing `</textarea>` tag gets misinterpreted.

### Expected behavior

The compiler should correctly identify `<textarea>` as a special tag (similar to how it handles `<title>`) and properly parse its opening and closing tags. The content after `</textarea>` should be treated as separate elements, not as part of the textarea content.

### System Info
- Vue version: 3.x
- Node: 18.x

This seems to affect any template that uses textarea elements. Let me know if you need more details!

---
Repository: /testbed
