# Bug Report

### Describe the bug

I'm experiencing an issue with transitions when using `<Teleport>` components. The transition doesn't work properly when the teleported content is wrapped in a transition component - the enter/leave animations are not being applied correctly.

### Reproduction

```vue
<template>
  <Transition name="fade">
    <Teleport to="body">
      <div v-if="show">Teleported content</div>
    </Teleport>
  </Transition>
</template>

<script setup>
import { ref } from 'vue'

const show = ref(true)

// Toggle to see transition
setTimeout(() => {
  show.value = false
}, 1000)
</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
```

### Expected behavior

The teleported content should animate in and out with the fade transition. Currently the content appears/disappears instantly without any transition animation.

This was working fine before, but seems to have broken recently. The transition works normally when not using Teleport.

### System Info
- Vue version: 3.x
- Browser: Chrome 121

---
Repository: /testbed
