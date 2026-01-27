# Bug Report

### Describe the bug

I'm experiencing an issue with SFC (Single File Component) parsing where the compiler is incorrectly identifying elements as being in the SFC root context. This causes unexpected behavior when parsing nested elements in SFC templates.

### Reproduction

```vue
<template>
  <div>
    <span>nested content</span>
  </div>
</template>
```

When the compiler processes this SFC, nested elements (like the `<span>` inside `<div>`) are being treated as if they're at the root level of the SFC, which leads to incorrect parsing behavior.

The issue seems to be related to how the parser determines whether it's currently processing elements at the SFC root level vs. nested elements within the template.

### Expected behavior

Only the actual root-level elements of an SFC (like the `<template>`, `<script>`, `<style>` tags themselves) should be considered as being in the SFC root context. Nested elements inside the template should be treated as regular nested elements.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

---
Repository: /testbed
