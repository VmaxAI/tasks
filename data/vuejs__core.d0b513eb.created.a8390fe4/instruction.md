# Bug Report

### Describe the bug
When using `v-model` with radio buttons, the comparison logic seems to have changed and is now causing issues with certain value types. Radio buttons with numeric values (like `0` or `1`) are not being properly selected when the bound value matches.

### Reproduction
```vue
<template>
  <div>
    <input type="radio" v-model="selected" :value="0" /> Option 0
    <input type="radio" v-model="selected" :value="1" /> Option 1
  </div>
</template>

<script setup>
import { ref } from 'vue'

const selected = ref(0)
// Expected: First radio should be checked
// Actual: No radio is checked
</script>
```

Also having issues when the value is a string that looks like a number:
```vue
<input type="radio" v-model="choice" value="0" />
<input type="radio" v-model="choice" value="1" />

// When choice = '0', the radio isn't selected properly
```

### Expected behavior
Radio buttons should be selected when their value matches the v-model bound value, regardless of whether it's a number, string, or other type. The previous loose equality comparison handled these cases correctly.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox

---
Repository: /testbed
