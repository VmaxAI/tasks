# Bug Report

### Describe the bug

When using `defineExpose()` in a script setup component, I'm getting an incorrect "duplicate defineExpose() call" error even though I'm only calling it once in my component.

### Reproduction

```vue
<script setup>
import { ref } from 'vue'

const count = ref(0)

defineExpose({
  count
})
</script>
```

The compiler throws an error saying there's a duplicate `defineExpose()` call, but there's clearly only one call in the component.

### Expected behavior

The component should compile successfully without any errors since there's only a single `defineExpose()` call.

### System Info
- Vue version: 3.x
- Using script setup with SFC compiler

---
Repository: /testbed
