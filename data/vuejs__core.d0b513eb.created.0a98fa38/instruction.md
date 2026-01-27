# Bug Report

### Describe the bug

I'm experiencing an issue with `v-model` on radio button inputs. The radio buttons are not being checked correctly when the component initializes, and they're also not responding to user clicks as expected.

### Reproduction

```vue
<template>
  <div>
    <input type="radio" v-model="selected" value="option1" />
    <input type="radio" v-model="selected" value="option2" />
    <input type="radio" v-model="selected" value="option3" />
  </div>
</template>

<script setup>
import { ref } from 'vue'

const selected = ref('option2')
</script>
```

### Expected behavior

- When the component loads, the radio button with `value="option2"` should be checked since that matches the initial value of `selected`
- When I click on a different radio button, it should become checked and update the `selected` value accordingly

### Actual behavior

- The wrong radio button is checked on initial render (the one that doesn't match the model value)
- Clicking on radio buttons doesn't properly update which one is selected

This seems to have broken recently. Radio buttons were working fine before but now the checked state is inverted or something.

---
Repository: /testbed
