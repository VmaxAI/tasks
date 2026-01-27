# Bug Report

### Describe the bug

I'm experiencing an issue with fragment removal in the DOM. When a fragment component is unmounted or removed, not all of its child nodes are being properly removed from the DOM. The first child node of the fragment remains in the DOM even after the fragment should be completely removed.

### Reproduction

```vue
<template>
  <button @click="toggle">Toggle Fragment</button>
  <template v-if="show">
    <div>First child</div>
    <div>Second child</div>
    <div>Third child</div>
  </template>
</template>

<script setup>
import { ref } from 'vue'

const show = ref(true)

function toggle() {
  show.value = !show.value
}
</script>
```

Steps to reproduce:
1. Render a fragment with multiple child elements
2. Toggle the fragment off (unmount it)
3. Inspect the DOM

### Expected behavior

All child nodes of the fragment should be removed from the DOM when the fragment is unmounted. The DOM should be clean with no leftover elements.

### Actual behavior

The first child element of the fragment remains in the DOM after unmounting. Only the subsequent children and the end marker are removed correctly.

This appears to be a regression as fragments were working correctly in previous versions.

---
Repository: /testbed
