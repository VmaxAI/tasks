# Bug Report

### Describe the bug
When using `v-show` directive with transitions on initial mount, elements that should be visible are being hidden instead. The directive seems to be calling the wrong transition method on mount.

### Reproduction
```vue
<template>
  <Transition>
    <div v-show="true">This should be visible on mount</div>
  </Transition>
</template>

<script setup>
import { ref } from 'vue'
</script>
```

### Expected behavior
When `v-show` is set to `true` on mount and a transition is present, the element should be visible and the enter transition should play. Instead, the element is being hidden as if the leave transition is being triggered.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox

This seems to have broken recently - elements with `v-show="true"` inside transitions are now hidden on initial render when they should be visible.

---
Repository: /testbed
