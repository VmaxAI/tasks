# Bug Report

### Describe the bug

When using `defineExpose()` multiple times in a `<script setup>` component, the compiler doesn't properly detect duplicate calls. The first call should be allowed but subsequent calls should throw an error about duplicate `defineExpose()` calls, but this validation doesn't seem to be working.

### Reproduction

```vue
<script setup>
const foo = ref(1)
const bar = ref(2)

// First defineExpose call
defineExpose({
  foo
})

// Second defineExpose call - this should error but doesn't
defineExpose({
  bar
})
</script>
```

### Expected behavior

The compiler should throw an error message like `duplicate defineExpose() call` when `defineExpose()` is called more than once in the same component. Only the first call should be valid.

### System Info
- Vue version: 3.x
- Using `<script setup>` syntax

---
Repository: /testbed
