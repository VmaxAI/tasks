# Bug Report

### Describe the bug

I'm experiencing an issue with `v-if`/`v-else-if`/`v-else` directives when using the `key` attribute. The conditional rendering doesn't work correctly when elements have keys with the same value - they're being treated as different elements instead of the same one.

### Reproduction

```vue
<template>
  <div v-if="show" key="same-key">
    Content A
  </div>
  <div v-else key="same-key">
    Content B
  </div>
</template>

<script setup>
import { ref } from 'vue'
const show = ref(true)
</script>
```

When toggling `show`, the transition doesn't work as expected. It seems like Vue is not recognizing that both elements have the same key value and should be treated as the same element for transition purposes.

### Expected behavior

Elements with identical `key` attribute values in `v-if`/`v-else` blocks should be recognized as the same element, allowing proper transitions and element reuse.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

---
Repository: /testbed
