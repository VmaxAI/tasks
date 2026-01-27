# Bug Report

### Describe the bug

I'm experiencing an issue with KeepAlive components where they're being activated even when they shouldn't be. It seems like components that aren't wrapped in `<KeepAlive>` are incorrectly going through the activation path instead of the normal mount path.

### Reproduction

```js
<template>
  <component :is="currentComponent" />
</template>

<script setup>
import { ref } from 'vue'
import ComponentA from './ComponentA.vue'
import ComponentB from './ComponentB.vue'

const currentComponent = ref(ComponentA)

// Switch between components
setTimeout(() => {
  currentComponent.value = ComponentB
}, 1000)
</script>
```

When switching between components that are NOT wrapped in KeepAlive, the components seem to be going through the KeepAlive activation logic. This causes unexpected behavior where components that should be mounted fresh are instead being "activated".

### Expected behavior

Components that are not wrapped in `<KeepAlive>` should go through the normal mount lifecycle, not the KeepAlive activation path. Only components explicitly wrapped in `<KeepAlive>` should use the activate/deactivate logic.

### System Info
- Vue version: 3.x
- Node version: 18.x

---
Repository: /testbed
