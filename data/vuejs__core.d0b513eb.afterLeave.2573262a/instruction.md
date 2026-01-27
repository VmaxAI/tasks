# Bug Report

### Describe the bug

I'm experiencing an issue with the `out-in` transition mode where components don't properly re-render after the leave transition completes. The new component should appear after the old one finishes leaving, but instead nothing happens and the UI stays in an empty/placeholder state.

### Reproduction

```vue
<template>
  <Transition mode="out-in">
    <component :is="currentComponent" :key="currentComponent" />
  </Transition>
</template>

<script setup>
import { ref } from 'vue'

const currentComponent = ref('ComponentA')

// Switch components
setTimeout(() => {
  currentComponent.value = 'ComponentB'
}, 1000)
</script>
```

### Expected behavior

When switching between components using `out-in` mode:
1. The current component should play its leave transition
2. After the leave transition completes, the component should be removed
3. The new component should immediately mount and play its enter transition

Instead, after step 2, the new component doesn't appear and the transition seems to get stuck.

### System Info
- Vue version: 3.x
- Transition mode: out-in

This seems to happen specifically with the `out-in` mode. The `in-out` mode and default mode work fine.

---
Repository: /testbed
