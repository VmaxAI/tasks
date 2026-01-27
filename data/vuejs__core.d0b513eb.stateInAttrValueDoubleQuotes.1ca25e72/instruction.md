# Bug Report

### Describe the bug

I'm experiencing an issue with template parsing when using double-quoted attribute values. It seems like the parser is treating double quotes incorrectly and getting confused about where the attribute value ends.

### Reproduction

```vue
<template>
  <div class="my-class" id="test-id">
    <span title="Hello World">Text</span>
  </div>
</template>
```

When parsing templates with attributes that use double quotes, the parser doesn't correctly identify the closing quote. This causes attributes to be parsed incorrectly or the parser to fail entirely.

### Expected behavior

Double-quoted attribute values should be parsed correctly, with the parser recognizing the closing double quote and properly extracting the attribute value.

For example:
- `class="my-class"` should parse with value `my-class`
- `title="Hello World"` should parse with value `Hello World`

### System Info
- Vue version: 3.x
- Build tool: Vite

This is breaking template compilation for components that use double-quoted attributes, which is pretty much the standard way of writing Vue templates.

---
Repository: /testbed
