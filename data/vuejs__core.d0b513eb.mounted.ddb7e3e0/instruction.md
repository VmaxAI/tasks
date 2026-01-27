# Bug Report

### Describe the bug

The `v-show` directive is not working correctly when mounting elements with transitions. Elements that should be visible on mount are not appearing, and elements that should be hidden are being shown instead.

### Reproduction

```vue
<template>
  <Transition>
    <div v-show="isVisible">This should be visible</div>
  </Transition>
</template>

<script setup>
import { ref } from 'vue'

const isVisible = ref(true)
</script>
```

When the component mounts with `isVisible` set to `true`, the element doesn't appear as expected. The transition seems to be triggered incorrectly during the initial mount phase.

### Expected behavior

When `v-show` is set to `true` on mount with a transition, the element should be visible and the enter transition should play. When set to `false`, the element should be hidden without triggering the enter transition.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox

---
Repository: /testbed
