# Bug Report

### Describe the bug

I'm experiencing an issue with the SFC compiler where imports are being incorrectly tree-shaken even when they're actively used in the template. This is causing components, directives, and other imported resources to be removed from the compiled output, leading to runtime errors.

### Reproduction

```vue
<script setup>
import { MyComponent } from './MyComponent.vue'
import { myDirective } from './directives'
</script>

<template>
  <MyComponent v-my-directive />
</template>
```

After compilation, the imports are being removed even though they're clearly referenced in the template. This results in undefined component/directive errors at runtime.

### Expected behavior

Imports that are used in the template should be preserved during compilation. The compiler should correctly detect template usage and keep the necessary imports in the output.

### System Info
- Vue version: 3.x
- Build tool: Vite

This seems to have started happening recently and is breaking existing code that was working fine before. Any imports referenced in the template are getting stripped out.

---
Repository: /testbed
