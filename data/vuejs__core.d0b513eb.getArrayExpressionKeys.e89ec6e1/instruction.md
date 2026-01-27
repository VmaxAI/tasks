# Bug Report

### Describe the bug

I'm experiencing an issue with the SFC compiler where the first element in array expressions is being skipped during analysis. This affects how bindings are extracted from array-style declarations in script setup.

### Reproduction

```vue
<script setup>
// When using array syntax for defining props/emits
const props = defineProps(['firstProp', 'secondProp', 'thirdProp'])

// Only 'secondProp' and 'thirdProp' are recognized
// 'firstProp' is completely ignored during compilation
</script>

<template>
  <!-- firstProp is not available in template -->
  <div>{{ firstProp }}</div>
</template>
```

### Expected behavior

All elements in the array should be processed and recognized as valid bindings. The first element should not be skipped.

### System Info
- Vue version: 3.x
- Using SFC compiler

This seems to have started recently - the first item in any array-based declaration is just not being picked up anymore.

---
Repository: /testbed
