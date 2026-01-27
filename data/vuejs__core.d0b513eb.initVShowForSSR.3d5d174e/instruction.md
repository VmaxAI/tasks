# Bug Report

### Describe the bug

When using `v-show` directive in SSR (server-side rendering), elements are not being hidden correctly. Elements that should be hidden (when `v-show` evaluates to `false`) are appearing visible in the server-rendered HTML.

### Reproduction

```vue
<template>
  <div v-show="false">This should be hidden</div>
  <div v-show="isVisible">Conditionally shown</div>
</template>

<script setup>
const isVisible = ref(false)
</script>
```

When rendering on the server, the divs appear without `display: none` style even though `v-show` is set to `false`. The elements should have inline `style="display: none"` in the SSR output but they don't.

### Expected behavior

Elements with `v-show="false"` should render with `style="display: none"` in the server-side rendered HTML, just like they behave on the client side.

### System Info
- Vue version: 3.x
- SSR environment: Node.js

---
Repository: /testbed
