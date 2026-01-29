# Bug Report

### Describe the bug

Template refs are not being set correctly when using string refs in the template. The ref value appears to be `undefined` instead of the expected DOM element or component instance.

### Reproduction

```vue
<template>
  <div ref="myDiv">Hello</div>
  <button @click="checkRef">Check Ref</button>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const myDiv = ref(null)

function checkRef() {
  console.log('Ref value:', myDiv.value) // Expected: div element, Actual: undefined
}

onMounted(() => {
  console.log('On mounted:', myDiv.value) // Also undefined
})
</script>
```

### Expected behavior

The `myDiv` ref should contain a reference to the actual DOM element after the component is mounted. Clicking the button should log the div element, not `undefined`.

### System Info
- Vue version: 3.x
- Browser: Chrome 121

This seems to have started happening recently. The refs were working fine before and now they're consistently undefined.

---
Repository: /testbed
