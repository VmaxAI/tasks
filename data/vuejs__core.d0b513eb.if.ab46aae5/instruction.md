# Bug Report

### Describe the bug

I'm encountering a critical issue with the compiler after a recent update. The application fails to build and throws syntax errors when processing template expressions with scoped variables.

### Reproduction

```js
<template>
  <div v-for="item in items" :key="item.id">
    {{ item.name }}
  </div>
</template>

<script setup>
const items = ref([
  { id: 1, name: 'Item 1' },
  { id: 2, name: 'Item 2' }
])
</script>
```

When trying to compile this component, the build process fails with unexpected syntax errors. The same code was working fine in the previous version.

### Expected behavior

The template should compile successfully and the component should render the list of items without any build errors.

### System Info
- Vue version: 3.x
- Node: v18.x
- Build tool: Vite

This is blocking our production deployment. Any help would be appreciated!

---
Repository: /testbed
