# Bug Report

### Describe the bug

I'm encountering an issue with the SFC compiler when using both `<script>` and `<script setup>` blocks with different language types. The compiler is throwing an error even when the language types are actually the same.

### Reproduction

```vue
<template>
  <div>Hello</div>
</template>

<script lang="ts">
export default {
  name: 'MyComponent'
}
</script>

<script setup lang="ts">
import { ref } from 'vue'
const count = ref(0)
</script>
```

### Expected behavior

The component should compile successfully since both script blocks use the same language (`ts`). The error message states that `<script>` and `<script setup>` must have the same language type, but they do have the same language type in this case.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-sfc

This seems like it might be a regression in the validation logic. The error is being thrown incorrectly when the languages actually match.

---
Repository: /testbed
