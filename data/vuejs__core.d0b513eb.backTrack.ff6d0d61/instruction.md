# Bug Report

### Describe the bug

I'm experiencing an issue with template parsing where certain character sequences in templates are being incorrectly parsed. It seems like the parser is not correctly backtracking through the input string when searching for specific characters.

### Reproduction

```vue
<template>
  <div>
    <!-- Complex nested structure with special characters -->
    <span>{{ message }}</span>
  </div>
</template>
```

When the template contains certain patterns or character sequences, the parser appears to traverse the input in the wrong direction or stops at incorrect positions. This leads to malformed AST nodes or parsing errors that shouldn't occur.

### Expected behavior

The parser should correctly identify and backtrack to find matching characters in the template string, regardless of the complexity of the template structure.

### System Info
- Vue version: 3.x
- Node version: 18.x

---
Repository: /testbed
