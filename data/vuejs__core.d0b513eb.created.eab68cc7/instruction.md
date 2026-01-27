# Bug Report

### Describe the bug

I'm experiencing an issue with `v-model` on radio button inputs. When the bound value is a number but the radio button's value attribute is a string representation of that number (or vice versa), the radio button doesn't get checked properly on initial render.

### Reproduction

```vue
<template>
  <input type="radio" v-model="selected" value="1" />
  <input type="radio" v-model="selected" value="2" />
</template>

<script setup>
import { ref } from 'vue'

const selected = ref(1) // number
</script>
```

In this case, even though `selected` is `1` (number) and one of the radio buttons has `value="1"` (string), the radio button doesn't get checked initially. It seems like the comparison is now strict instead of loose, so `1 !== "1"` fails.

This used to work fine before - Vue would handle the type coercion automatically when comparing values.

### Expected behavior

The radio button with `value="1"` should be checked when the model value is the number `1`. Vue should perform loose equality comparison to handle common cases where form values (strings) need to match against numeric model values.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox

---
Repository: /testbed
