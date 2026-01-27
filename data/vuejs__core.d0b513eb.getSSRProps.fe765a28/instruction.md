# Bug Report

### Describe the bug

I'm experiencing an issue with `v-model` on radio buttons during SSR. The radio buttons are getting checked in the wrong state - they appear checked when they shouldn't be, and unchecked when they should be checked.

### Reproduction

```vue
<template>
  <div>
    <input type="radio" v-model="selected" value="option1" />
    <input type="radio" v-model="selected" value="option2" />
  </div>
</template>

<script setup>
import { ref } from 'vue'

const selected = ref('option1')
</script>
```

When rendering this on the server:
1. The first radio button (value="option1") should be checked since `selected` is 'option1'
2. Instead, the second radio button (value="option2") gets the checked attribute
3. The behavior is completely inverted from what's expected

### Expected behavior

Radio buttons should be checked when their value matches the v-model binding value during SSR, not the opposite.

### System Info
- Vue version: 3.x
- SSR environment: Node.js

This seems to have broken recently. The client-side hydration works fine, but the initial SSR output has the wrong radio button selected.

---
Repository: /testbed
