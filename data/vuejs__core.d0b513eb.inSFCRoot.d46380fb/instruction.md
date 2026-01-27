# Bug Report

### Describe the bug

I'm encountering an issue with Single File Component (SFC) parsing where the parser doesn't correctly identify when it's at the root level of an SFC. This seems to affect how certain template syntax is handled at the top level of SFC templates.

### Reproduction

```vue
<template>
  <div>Content here</div>
</template>
```

When parsing SFC templates, the behavior at the root level appears incorrect. Elements that should be recognized as being at the SFC root level are not being treated as such, which can lead to parsing inconsistencies.

### Expected behavior

The parser should correctly identify when it's processing elements at the root level of an SFC (when the element stack is empty or just starting). Root-level elements in SFC templates should be handled differently from nested elements.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

This might be related to how the tokenizer tracks the parsing context for SFCs. The issue becomes apparent when working with templates that have specific root-level requirements.

---
Repository: /testbed
