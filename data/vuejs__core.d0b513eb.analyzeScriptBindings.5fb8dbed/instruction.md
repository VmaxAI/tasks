# Bug Report

### Describe the bug

I'm experiencing an issue with SFC script analysis where bindings are not being detected correctly in `<script>` blocks. It seems like the compiler is failing to recognize exported default objects and their bindings.

### Reproduction

```vue
<script>
export default {
  data() {
    return {
      message: 'Hello'
    }
  },
  methods: {
    updateMessage() {
      this.message = 'Updated'
    }
  }
}
</script>

<template>
  <div>{{ message }}</div>
</template>
```

When compiling this SFC, the bindings from the exported default object (like `message` and `updateMessage`) are not being properly analyzed. This causes issues with template compilation and binding resolution.

### Expected behavior

The `analyzeScriptBindings` function should correctly identify and extract bindings from the exported default object in `<script>` blocks. All data properties and methods should be recognized as valid bindings.

### System Info
- Vue version: 3.x
- Using SFC compiler

This seems to have started recently. The compiler appears to be skipping over the default export entirely instead of analyzing it for bindings.

---
Repository: /testbed
