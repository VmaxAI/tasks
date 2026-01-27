# Bug Report

### Describe the bug

The `.right` modifier on `v-on` directive is not working correctly for mouse events. When I try to use `@click.right` or `@mousedown.right` to listen for right-click events, it's triggering on left clicks instead (or all clicks).

### Reproduction

```vue
<template>
  <div @click.right="handleRightClick">
    Right click me
  </div>
</template>

<script setup>
function handleRightClick() {
  console.log('Right click detected')
}
</script>
```

When I left-click on the div, the handler is being called when it shouldn't be. The `.right` modifier should only trigger on right mouse button clicks (button 2), but it seems to be behaving incorrectly.

### Expected behavior

The event handler should only fire when the right mouse button is clicked. Left clicks and middle clicks should be ignored when using the `.right` modifier.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox (tested on both)

This seems like a regression - it was working fine in previous versions.

---
Repository: /testbed
