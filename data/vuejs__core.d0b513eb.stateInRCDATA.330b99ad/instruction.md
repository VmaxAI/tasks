# Bug Report

### Describe the bug

I'm encountering an issue with parsing RCDATA elements (like `<title>` and `<textarea>`) in the template compiler. When there are certain patterns of `<` characters in the content, the parser seems to get stuck or behave incorrectly.

### Reproduction

```vue
<template>
  <title><<script</title>
</template>
```

Or with textarea:

```vue
<template>
  <textarea>Some text with << characters</textarea>
</template>
```

The content inside these tags isn't being parsed correctly when there are multiple `<` characters or patterns like `<<` followed by tag-like sequences.

### Expected behavior

The parser should correctly handle text content within RCDATA elements regardless of `<` character patterns. The content should be treated as text and not cause parsing issues.

### System Info
- Vue version: 3.x
- Using SFC compiler

---
Repository: /testbed
