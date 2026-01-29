# Bug Report

### Describe the bug

When using `<KeepAlive>` components, the `onMounted` hook is being called multiple times when switching between cached components. The mounted hook should only fire once when the component is first mounted, not every time it's activated from the cache.

### Reproduction

```vue
<template>
  <KeepAlive>
    <component :is="currentComponent" />
  </KeepAlive>
</template>

<script setup>
import { ref } from 'vue'

const currentComponent = ref('ComponentA')

// ComponentA definition
const ComponentA = {
  setup() {
    onMounted(() => {
      console.log('ComponentA mounted')
    })
  }
}

// Switch between components
setTimeout(() => {
  currentComponent.value = 'ComponentB'
}, 1000)

setTimeout(() => {
  currentComponent.value = 'ComponentA' // onMounted fires again!
}, 2000)
</script>
```

### Expected behavior

The `onMounted` hook should only be called once when the component is initially mounted. When a component is reactivated from KeepAlive cache, only `onActivated` should be called, not `onMounted`.

### System Info
- Vue version: 3.x
- Environment: Browser

---
Repository: /testbed
