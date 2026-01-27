# Bug Report

### Describe the bug

When using `v-show` directive with server-side rendering (SSR), the display logic appears to be inverted. Elements that should be visible are being hidden, and elements that should be hidden are being shown.

### Reproduction

```vue
<template>
  <div v-show="true">Should be visible</div>
  <div v-show="false">Should be hidden</div>
</template>
```

When rendering this on the server:
- The first div (with `v-show="true"`) gets `display: none` applied and is hidden
- The second div (with `v-show="false"`) renders without any display style and is visible

### Expected behavior

Elements with `v-show="true"` should be visible (no display style applied), and elements with `v-show="false"` should have `display: none` applied to hide them.

This seems to only affect SSR - client-side rendering works as expected.

### System Info
- Vue version: 3.x
- SSR: Yes

---
Repository: /testbed
