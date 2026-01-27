# Bug Report

### Describe the bug

I'm experiencing an issue with the template compiler where it's not correctly handling special tags in SFC (Single File Component) root contexts. The parser seems to be treating tags differently than expected when they appear at the root level of an SFC.

### Reproduction

```vue
<template>
  <div>Test</div>
</template>

<script>
export default {
  name: 'TestComponent'
}
</script>
```

When compiling this SFC, the parser doesn't properly recognize the root-level tags. It appears that the logic for determining whether we're in an SFC root context vs. regular HTML mode has gotten inverted somehow.

### Expected behavior

The compiler should correctly identify and parse root-level tags in SFC files, treating `<template>`, `<script>`, and `<style>` tags appropriately based on the SFC context. Special tags like `<script>` and `<style>` should be handled as RAWTEXT, while `<template>` tags should follow normal parsing rules unless they have a non-HTML lang attribute.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

This seems to have broken recently - the template compilation is not working as it did before.

---
Repository: /testbed
