# Bug Report

### Describe the bug

I'm experiencing an issue with `v-model` directive in SSR (Server-Side Rendering) mode. When using `v-model` with dynamic components, the model binding doesn't work correctly during server-side rendering. The props that should be generated for SSR are not being created properly.

### Reproduction

```vue
<template>
  <component :is="dynamicComponent" v-model="value" />
</template>

<script setup>
import { ref } from 'vue'

const dynamicComponent = 'input'
const value = ref('test')
</script>
```

When rendering this on the server, the `v-model` binding seems to be skipped or not applied correctly. The expected SSR props (like `value` and event handlers) are missing from the rendered output.

### Expected behavior

The `v-model` directive should work correctly with dynamic components during SSR, generating the appropriate props for the bound element type (input, select, textarea, etc.). The server-rendered HTML should include the correct attributes and values.

### System Info
- Vue version: 3.x
- Environment: SSR/Node.js

This appears to have started happening recently. The client-side hydration works fine, but the initial server render is missing the model binding.

---
Repository: /testbed
