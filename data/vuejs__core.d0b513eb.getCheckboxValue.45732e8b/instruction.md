# Bug Report

### Describe the bug

When using `v-model` with checkbox inputs that have custom `true-value` and `false-value` bindings, the values are being swapped. Checking the checkbox assigns the false value to the model, and unchecking it assigns the true value instead.

### Reproduction

```vue
<template>
  <input 
    type="checkbox" 
    v-model="selected"
    true-value="yes"
    false-value="no"
  />
  <p>Selected: {{ selected }}</p>
</template>

<script setup>
import { ref } from 'vue'
const selected = ref('no')
</script>
```

**Steps:**
1. Start with checkbox unchecked (selected = 'no')
2. Check the checkbox
3. Expected: selected = 'yes'
4. Actual: selected = 'no'

The behavior is completely inverted - checking gives you the false-value and unchecking gives you the true-value.

### Expected behavior

When a checkbox with custom true-value/false-value is checked, the model should be set to the true-value. When unchecked, it should be set to the false-value.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox

---
Repository: /testbed
