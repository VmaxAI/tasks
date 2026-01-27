# Bug Report

### Describe the bug

I'm experiencing an issue with `v-show` directive during server-side rendering. Elements that should be visible are being hidden, and elements that should be hidden are also being hidden. It seems like the visibility logic is inverted or broken.

### Reproduction

```vue
<template>
  <!-- This element should be visible but is hidden -->
  <div v-show="true">Should be visible</div>
  
  <!-- This element should be hidden and is hidden (correct) -->
  <div v-show="false">Should be hidden</div>
</template>
```

When rendering on the server, both elements end up with `display: none` in their inline styles, even though the first one should be visible.

### Expected behavior

- When `v-show="true"`, the element should be visible (no `display: none` style)
- When `v-show="false"`, the element should have `display: none` style

Currently, all elements seem to get `display: none` regardless of the condition value.

### System Info

- Vue version: 3.x
- Rendering: SSR

---
Repository: /testbed
