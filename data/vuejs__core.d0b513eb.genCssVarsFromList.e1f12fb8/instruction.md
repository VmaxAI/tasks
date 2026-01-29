# Bug Report

### Describe the bug

CSS variables generated from `v-bind` in `<style>` blocks are missing the `--` prefix during server-side rendering (SSR). When using CSS custom properties with `v-bind()` in SFC styles, the generated variable names don't include the proper prefix in SSR mode, causing styles to not apply correctly on the server-rendered output.

### Reproduction

```vue
<template>
  <div class="container">Hello</div>
</template>

<script setup>
const color = 'red'
</script>

<style scoped>
.container {
  color: v-bind(color);
}
</style>
```

When rendering this component on the server, the CSS variable is generated without the `--` prefix, resulting in invalid CSS variable references.

### Expected behavior

CSS variables should be generated with the `--` prefix in both client-side and server-side rendering modes. The variable name format should be consistent regardless of the rendering context.

### System Info
- Vue version: 3.x
- Rendering mode: SSR

---
Repository: /testbed
