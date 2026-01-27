# Bug Report

### Describe the bug

The `v-show` directive is not preserving the original display style correctly when toggling element visibility. When an element has an inline `display` style set (e.g., `display: flex` or `display: inline-block`), the directive fails to restore it properly after hiding and showing the element again.

### Reproduction

```html
<template>
  <div>
    <div v-show="visible" style="display: flex">
      This should be display: flex when visible
    </div>
    <button @click="visible = !visible">Toggle</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const visible = ref(true)
</script>
```

Steps to reproduce:
1. Create an element with an inline display style (e.g., `display: flex`)
2. Apply `v-show` directive with a reactive value
3. Toggle the visibility
4. Check the element's display style after showing it again

### Expected behavior

When the element is shown again, it should restore the original `display: flex` style. Instead, it appears to be losing the original display value and defaults to an empty string or incorrect value.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox

---
Repository: /testbed
