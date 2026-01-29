# Bug Report

### Describe the bug

When using `defineExpose()` multiple times in a `<script setup>` component, the compiler doesn't properly report a duplicate call error. The first duplicate call should be caught and flagged, but it seems the error detection logic isn't working as expected.

### Reproduction

```vue
<script setup>
defineExpose({
  foo: 'bar'
})

defineExpose({
  baz: 'qux'
})
</script>
```

### Expected behavior

The compiler should throw an error on the second `defineExpose()` call indicating that duplicate calls are not allowed. Currently, the error detection appears to be inconsistent or not triggering properly.

### System Info
- Vue version: 3.x

---
Repository: /testbed
