# Bug Report

### Describe the bug

When using `<KeepAlive>` with components that have `onMounted` hooks, the mounted hooks are being called multiple times when toggling between cached components. The `onMounted` lifecycle hook should only fire once when the component is first mounted, not every time it's activated from the cache.

### Reproduction

```vue
<template>
  <KeepAlive>
    <component :is="currentView" />
  </KeepAlive>
  <button @click="toggle">Toggle</button>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const currentView = ref('ComponentA')

const ComponentA = {
  setup() {
    onMounted(() => {
      console.log('ComponentA mounted')
    })
    return () => h('div', 'Component A')
  }
}

const ComponentB = {
  setup() {
    return () => h('div', 'Component B')
  }
}

function toggle() {
  currentView.value = currentView.value === 'ComponentA' ? 'ComponentB' : 'ComponentA'
}
</script>
```

Steps to reproduce:
1. Create a component with an `onMounted` hook wrapped in `<KeepAlive>`
2. Switch to another component
3. Switch back to the first component
4. Check the console - `onMounted` is called again

### Expected behavior

The `onMounted` hook should only be called once when the component is initially mounted, not when it's reactivated from the KeepAlive cache. Only `onActivated` should be called when returning to a cached component.

### System Info
- Vue version: 3.x

---
Repository: /testbed
