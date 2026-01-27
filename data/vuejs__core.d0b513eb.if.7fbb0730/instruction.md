# Bug Report

### Describe the bug

When using the `<Transition>` component, custom props passed to the component are not being forwarded correctly. Any additional props beyond the standard transition props (like `name`, `css`, `mode`, etc.) are being lost and don't get applied to the transition element.

### Reproduction

```vue
<template>
  <Transition 
    name="fade"
    custom-prop="test"
    data-id="123"
  >
    <div v-if="show">Content</div>
  </Transition>
</template>

<script setup>
import { ref } from 'vue'
const show = ref(true)
</script>
```

After rendering, the custom props (`custom-prop`, `data-id`) are not present on the transition element. This used to work in previous versions where non-transition-specific props would be passed through.

### Expected behavior

Custom props that are not part of the standard Transition props should be passed through to the underlying element, similar to how other components handle prop forwarding.

### System Info
- Vue version: 3.x
- Browser: Latest Chrome

---
Repository: /testbed
