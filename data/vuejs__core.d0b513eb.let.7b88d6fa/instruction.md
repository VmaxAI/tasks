# Bug Report

### Describe the bug

When using `defineEmits` with type-based declarations in SFC `<script setup>`, the emits are not being extracted correctly. It seems like the compiler is adding an unexpected emit entry when processing the type definition.

### Reproduction

```vue
<script setup lang="ts">
const emit = defineEmits<{
  update: [value: string]
  change: [value: number]
}>()
</script>
```

After compilation, the component seems to have an extra emit registered that shouldn't be there. This is causing issues when trying to validate emitted events or when inspecting the component's emit options.

### Expected behavior

Only the explicitly defined emits (`update` and `change` in the example above) should be registered. No additional or unexpected emit names should appear in the compiled output.

### System Info
- Vue version: 3.x
- Using TypeScript with SFC

---
Repository: /testbed
