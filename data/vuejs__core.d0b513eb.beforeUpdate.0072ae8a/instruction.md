# Bug Report

### Describe the bug
When using `v-model` with radio button inputs, the radio button doesn't update its checked state when the bound value changes. The radio button remains in its previous state even though the model value has been updated to match a different radio button's value.

### Reproduction
```vue
<template>
  <div>
    <input type="radio" v-model="selected" value="option1" />
    <input type="radio" v-model="selected" value="option2" />
    <button @click="selected = 'option2'">Select Option 2</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const selected = ref('option1')
</script>
```

Steps to reproduce:
1. Create radio buttons bound to the same v-model
2. Programmatically change the model value to match one of the radio button values
3. The radio button's checked state doesn't update to reflect the new value

### Expected behavior
When the model value is updated programmatically to match a radio button's value, that radio button should become checked and the previously checked radio button should become unchecked.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox

---
Repository: /testbed
