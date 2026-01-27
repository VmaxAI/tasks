# Bug Report

### Describe the bug

I'm experiencing an issue with unused import detection in SFC compiler. It seems like imports are being incorrectly marked as "used" even when they're not actually referenced anywhere in the template or script.

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

In this example, `someUnusedHelper` is imported but never used. The compiler should be able to detect this and potentially warn or tree-shake it, but it's not being flagged as unused.

### Expected behavior

The compiler should correctly identify when an import is not used in either the script or template, allowing for proper tree-shaking and unused import warnings.

### System Info
- Vue version: 3.x
- Using: Vite with vue-sfc-compiler

---
Repository: /testbed
