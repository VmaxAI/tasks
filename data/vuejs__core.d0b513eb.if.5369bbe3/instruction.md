# Bug Report

### Describe the bug

When using `defineEmits()` with both type parameters and runtime arguments in a Vue SFC, the compiler is not properly validating the usage and throwing an error when it should accept the configuration.

### Reproduction

```vue
<script setup lang="ts">
// This should throw an error but doesn't
const emit = defineEmits<{
  (e: 'update', value: string): void
}>(['update'])
</script>
```

### Expected behavior

The compiler should throw an error stating that `defineEmits()` cannot accept both type and non-type arguments at the same time. You should use either the type parameter syntax OR the runtime array syntax, but not both.

Currently, the validation logic seems inverted - it's not catching this invalid usage pattern.

### System Info
- Vue version: 3.x
- Using `<script setup>` with TypeScript

---
Repository: /testbed
