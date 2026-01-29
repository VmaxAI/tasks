# Bug Report

### Describe the bug

I'm encountering an issue with runtime type validation in SFC scripts. When defining props with a single type, the generated runtime type string is wrapped in array brackets `[]` when it shouldn't be.

### Reproduction

```vue
<script setup lang="ts">
defineProps<{
  value: string
}>()
</script>
```

The generated runtime type for the `value` prop is being output as `[string]` instead of just `string`.

### Expected behavior

For a single type, the runtime type string should be the type itself without array brackets. Array brackets should only be used when there are multiple types (union types).

Expected output: `string`
Actual output: `[string]`

### Additional context

This seems to affect any prop with a single type definition. Multiple types (like `string | number`) might be working correctly, but single types are incorrectly being wrapped in brackets.

---
Repository: /testbed
