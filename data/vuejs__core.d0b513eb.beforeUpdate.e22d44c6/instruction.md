# Bug Report

### Describe the bug

I'm experiencing an issue with `v-model` on `<select>` elements where the selected value doesn't update properly when the bound data changes. The select element seems to get stuck on the initial value and doesn't respond to programmatic updates to the model.

### Reproduction

```vue
<template>
  <select v-model="selectedValue">
    <option value="a">Option A</option>
    <option value="b">Option B</option>
    <option value="c">Option C</option>
  </select>
  <button @click="changeValue">Change to B</button>
</template>

<script setup>
import { ref } from 'vue'

const selectedValue = ref('a')

function changeValue() {
  selectedValue.value = 'b'
  // The select element doesn't update to show Option B selected
}
</script>
```

### Expected behavior

When `selectedValue` is updated programmatically, the `<select>` element should update to reflect the new value. The correct option should be visually selected in the dropdown.

### Additional context

This seems to have started happening recently. The initial value is set correctly when the component mounts, but subsequent updates to the reactive value don't propagate to the select element. Manually changing the select with the mouse still works and updates the model correctly, but the reverse direction (model → view) is broken.

---
Repository: /testbed
