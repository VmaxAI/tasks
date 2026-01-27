# Bug Report

### Describe the bug
HTML comments are not being parsed correctly in templates. The comment content appears to be truncated or includes extra characters at the end.

### Reproduction
```vue
<template>
  <!-- This is a test comment -->
  <div>Content</div>
</template>
```

When parsing templates with HTML comments, the comment content doesn't match what was written in the source. It seems like the parser is either cutting off the last character or including an extra character from the closing tag.

### Expected behavior
The comment content should be extracted exactly as written between `<!--` and `-->`, without any truncation or extra characters.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

---
Repository: /testbed
