# Bug Report

### Describe the bug

I'm experiencing an issue with props access in templates when using `defineProps()` with destructuring. When a prop is accessed in the template using its original name (not the destructured alias), the compiler seems to generate incorrect code or fails to properly handle the binding.

### Reproduction

```vue
<script setup lang="ts">
const { originalName: aliasedName } = defineProps<{
  originalName: string
}>()
</script>

<template>
  <!-- Accessing via original prop name in template -->
  <div>{{ originalName }}</div>
</template>
```

When the template tries to access `originalName` directly (the actual prop name), instead of the destructured alias `aliasedName`, the generated code doesn't handle this correctly. 

### Expected behavior

The template should be able to access props using their original names even when they've been destructured with aliases in the script setup. The compiler should properly resolve the binding and generate the correct `__props` access expression.

### System Info
- Vue version: 3.x
- Using `<script setup>` with TypeScript

---
Repository: /testbed
