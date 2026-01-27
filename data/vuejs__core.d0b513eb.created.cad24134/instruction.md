# Bug Report

### Describe the bug

I'm experiencing an issue with `v-model` on text inputs where the input stops updating when typing with an IME (Input Method Editor) for languages like Chinese, Japanese, or Korean. The model value doesn't update during composition, which makes the input completely unusable for these languages.

### Reproduction

```vue
<template>
  <input v-model="text" type="text" />
  <p>Value: {{ text }}</p>
</template>

<script setup>
import { ref } from 'vue'
const text = ref('')
</script>
```

Steps to reproduce:
1. Use an IME input method (e.g., Chinese Pinyin, Japanese Hiragana)
2. Start typing with the IME
3. Notice that the input field doesn't update and the model value remains empty

### Expected behavior

The input should update normally during IME composition. The model value should reflect what's being typed even before the composition is finalized. This worked correctly in previous versions.

### System Info
- Vue version: 3.x
- Browser: Chrome/Safari
- OS: macOS

This is particularly problematic for users in Asian markets where IME input is essential. Any help would be appreciated!

---
Repository: /testbed
