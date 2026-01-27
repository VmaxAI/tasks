# Bug Report

### Describe the bug

I'm experiencing an issue with the `<KeepAlive>` component where the `include` prop doesn't work as expected when using regex patterns. Components that should be cached are not being cached, and it seems like the matching logic is inverted.

### Reproduction

```vue
<template>
  <KeepAlive :include="/^MyComponent/">
    <component :is="currentComponent" />
  </KeepAlive>
</template>

<script setup>
import { ref } from 'vue'
import MyComponent from './MyComponent.vue'
import OtherComponent from './OtherComponent.vue'

const currentComponent = ref(MyComponent)
</script>
```

When I switch between `MyComponent` and `OtherComponent`, the behavior is backwards:
- `MyComponent` (which matches the regex `/^MyComponent/`) is NOT being cached
- `OtherComponent` (which doesn't match) seems to be cached instead

### Expected behavior

Components whose names match the regex pattern in the `include` prop should be cached by KeepAlive. In this case, `MyComponent` should be cached since it matches `/^MyComponent/`, while `OtherComponent` should not be cached.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox

This is blocking our production deployment as we rely heavily on KeepAlive with regex patterns for conditional caching. Any help would be appreciated!

---
Repository: /testbed
