# Bug Report

### Describe the bug

When using components with props that have the same name as setup bindings, the template compiler is resolving references incorrectly. It seems like the priority order for checking bindings has changed, causing props to be resolved before setup refs/let bindings in some cases.

Additionally, I noticed that when using kebab-case component names in templates, the compiler is returning the wrong casing variant (PascalCase instead of camelCase or vice versa) when resolving setup references.

### Reproduction

```vue
<script setup>
import { ref } from 'vue'

const myValue = ref('from setup')
const props = defineProps({
  myValue: String  // same name as setup binding
})
</script>

<template>
  <!-- This should use the setup ref, but might be using the prop instead -->
  <div>{{ myValue }}</div>
</template>
```

Also happens with component references:

```vue
<script setup>
import MyComponent from './MyComponent.vue'
</script>

<template>
  <!-- Component name resolution seems backwards -->
  <my-component />
</template>
```

### Expected behavior

1. Setup bindings (refs, let) should be resolved before props when they have the same name
2. Component name casing should be resolved correctly (camelCase -> camelCase, PascalCase -> PascalCase)

### System Info
- Vue version: 3.x
- Build tool: Vite

This seems like it might be a regression in the template compiler's binding resolution logic.

---
Repository: /testbed
