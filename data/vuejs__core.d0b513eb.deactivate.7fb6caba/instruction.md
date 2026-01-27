# Bug Report

### Describe the bug

When using `<KeepAlive>` with components, the deactivated state is not being set correctly. After a component is deactivated, `instance.isDeactivated` remains `false` instead of being set to `true`, which causes issues with lifecycle hooks and component behavior.

### Reproduction

```vue
<template>
  <KeepAlive>
    <component :is="currentComponent" />
  </KeepAlive>
  <button @click="toggle">Toggle</button>
</template>

<script setup>
import { ref, onDeactivated } from 'vue'

const currentComponent = ref('ComponentA')

const toggle = () => {
  currentComponent.value = currentComponent.value === 'ComponentA' ? 'ComponentB' : 'ComponentA'
}

// In ComponentA:
onDeactivated(() => {
  // This hook fires but the component instance still reports isDeactivated = false
  console.log('Component deactivated')
})
</script>
```

### Expected behavior

When a component wrapped in `<KeepAlive>` is deactivated (switched away from), the component instance's `isDeactivated` property should be set to `true`. This is important for proper lifecycle management and for components to know their current state.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox

---
Repository: /testbed
