# Bug Report

### Describe the bug

I'm experiencing issues with component updates during Hot Module Replacement (HMR). When making changes to a component and the HMR kicks in, the component doesn't update properly and I'm seeing stale data or missing updates in nested components.

### Reproduction

```js
// ParentComponent.vue
<template>
  <div>
    <ChildComponent />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import ChildComponent from './ChildComponent.vue'

const data = ref({ value: 'initial' })
</script>

// ChildComponent.vue
<template>
  <div>{{ message }}</div>
</template>

<script setup>
import { ref } from 'vue'
const message = ref('Hello')
</script>
```

Steps to reproduce:
1. Start dev server with HMR enabled
2. Make a change to ChildComponent
3. Save the file to trigger HMR
4. The component doesn't update correctly or shows stale content

This seems to happen specifically during HMR updates when there are parent-child component relationships. The updates work fine on initial mount or full page refresh, but HMR updates are broken.

### Expected behavior

Components should update correctly during HMR, reflecting the latest changes made to the source files.

### System Info
- Vue version: 3.x
- Dev environment: Vite
- Browser: Chrome

---
Repository: /testbed
