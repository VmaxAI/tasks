# Bug Report

### Describe the bug

The compiler is failing to process template code with block statements. I'm getting syntax errors when trying to compile components that have certain block-level scoping patterns.

### Reproduction

```js
<template>
  <div v-if="condition">
    {{ message }}
  </div>
</template>

<script setup>
import { ref } from 'vue'

const condition = ref(true)
const message = ref('Hello')

if (condition.value) {
  const localVar = 'test'
  message.value = localVar
}
</script>
```

When compiling this component, the compiler throws an error and fails to build. The issue seems related to how block-level variables are being tracked.

### Expected behavior

The component should compile successfully and block-level variables should be properly scoped and tracked by the compiler.

### System Info
- Vue version: 3.x
- Node version: 18.x

This is blocking my project from building. Any help would be appreciated!

---
Repository: /testbed
