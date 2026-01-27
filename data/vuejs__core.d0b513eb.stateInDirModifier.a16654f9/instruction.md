# Bug Report

### Describe the bug
I'm experiencing an issue with directive modifiers in template compilation. When using multiple chained modifiers on a directive (e.g., `v-model.trim.lazy`), the parser seems to be including an extra character at the start of each modifier after the first one.

### Reproduction
```vue
<template>
  <input v-model.trim.lazy="value" />
</template>
```

When the template is compiled, the modifiers are being parsed incorrectly. The second modifier (and any subsequent ones) appear to have an extra dot character prepended to them.

For example:
- First modifier: `trim` ✓ (correct)
- Second modifier: `.lazy` ✗ (should be `lazy`)

### Expected behavior
Each modifier in a chain should be parsed cleanly without including the dot separator as part of the modifier name. The modifiers should be:
- `trim`
- `lazy`

Not:
- `trim`
- `.lazy`

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

This affects any directive that uses multiple modifiers chained together with dots.

---
Repository: /testbed
