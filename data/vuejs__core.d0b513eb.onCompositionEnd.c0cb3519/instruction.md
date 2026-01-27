# Bug Report

### Describe the bug

I'm experiencing an issue with `v-model` on text inputs when using IME (Input Method Editor) for languages like Chinese, Japanese, or Korean. After finishing IME composition, the input value doesn't update correctly in the bound data model.

### Reproduction

```vue
<template>
  <input v-model="text" />
  <p>Value: {{ text }}</p>
</template>

<script setup>
import { ref } from 'vue'
const text = ref('')
</script>
```

Steps to reproduce:
1. Use an IME (e.g., Chinese Pinyin input method)
2. Start typing with IME active
3. Select a character from the IME suggestions to complete composition
4. The displayed value in the `<p>` tag doesn't reflect the final composed character

### Expected behavior

When IME composition ends and a character is selected, the `v-model` binding should update immediately with the final composed text. The bound data should reflect the complete input including the composed characters.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox (any browser with IME support)
- OS: Windows/macOS with IME enabled

This is blocking our application from properly supporting international users who rely on IME for text input.

---
Repository: /testbed
