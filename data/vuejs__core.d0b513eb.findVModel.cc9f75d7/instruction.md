# Bug Report

### Describe the bug

When using multiple `v-model` directives on the same element in SSR mode, the wrong v-model is being selected. It appears that the first v-model is being used instead of the last one, which causes incorrect binding behavior.

### Reproduction

```vue
<template>
  <input 
    v-model.trim="firstName"
    v-model="lastName"
  />
</template>
```

In this case, the component should use `lastName` as the active v-model (the last one defined), but it seems to be using `firstName` instead.

### Expected behavior

When multiple v-models are present on the same element, the last one should take precedence, similar to how multiple bindings work in regular Vue templates. The SSR output should reflect the correct v-model binding.

### System Info
- Vue version: 3.x
- Environment: SSR

---
Repository: /testbed
