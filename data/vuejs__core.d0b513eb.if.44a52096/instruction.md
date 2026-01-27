# Bug Report

### Describe the bug

I'm experiencing an issue with transitions when using `<Teleport>` inside `<KeepAlive>`. The transition behavior seems broken - components are not transitioning properly when they should be getting the inner child for transition hooks.

### Reproduction

```vue
<template>
  <KeepAlive>
    <Teleport to="body">
      <Transition name="fade">
        <div v-if="show">Content</div>
      </Transition>
    </Teleport>
  </KeepAlive>
</template>

<script setup>
import { ref } from 'vue'

const show = ref(true)

// Toggle to see the issue
setTimeout(() => {
  show.value = false
}, 1000)
</script>
```

### Expected behavior

When using Teleport inside KeepAlive with transitions, the transition should work correctly and find the proper inner child node to apply transition hooks to.

### System Info

- Vue version: 3.x
- Browser: Chrome/Firefox

The transitions just don't seem to be applied correctly in this combination. It worked fine before but something seems to have changed with how inner children are resolved for KeepAlive components.

---
Repository: /testbed
