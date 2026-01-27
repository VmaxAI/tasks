# Bug Report

### Describe the bug

I'm unable to use `defineSlots()` in my SFC components anymore. When I try to add slot type definitions using `defineSlots()`, the compiler doesn't recognize it and the slots aren't being processed correctly.

### Reproduction

```vue
<script setup lang="ts">
const slots = defineSlots<{
  default(props: { msg: string }): any
  header(): any
}>()
</script>

<template>
  <div>
    <slot name="header" />
    <slot :msg="'hello'" />
  </div>
</template>
```

The `defineSlots()` call seems to be completely ignored by the compiler. The slots don't get their proper type definitions and the component behaves as if `defineSlots()` was never called.

### Expected behavior

The `defineSlots()` macro should be recognized and processed by the compiler, providing proper type checking for slot usage in the component.

### System Info
- Vue version: 3.x
- Using `<script setup>` with TypeScript

---
Repository: /testbed
