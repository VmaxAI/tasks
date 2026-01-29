# Bug Report

### Describe the bug

I'm encountering an issue with unused import detection in SFC compiler. It seems like imports are being incorrectly marked as "used" even when they're not actually referenced anywhere in the template or script.

### Reproduction

```vue
<script setup>
import { ref } from 'vue'
import { someUnusedHelper } from './utils'

const count = ref(0)
</script>

<template>
  <div>{{ count }}</div>
</template>
```

In this example, `someUnusedHelper` is imported but never used. However, the compiler doesn't seem to properly detect this as an unused import and may not warn about it or handle it correctly during the compilation process.

### Expected behavior

The compiler should correctly identify that `someUnusedHelper` is not used anywhere in the component and handle it appropriately (e.g., tree-shake it or warn about it).

### Additional context

This seems to affect the import usage checking logic. The issue appears to be related to how the compiler determines whether an imported identifier is actually referenced in the template.

---
Repository: /testbed
