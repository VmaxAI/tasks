# Bug Report

### Describe the bug

I'm experiencing an issue with component props merging in templates. When a component has multiple static props along with dynamic props (using `v-bind`), the static props seem to be duplicated or not properly merged in the compiled output.

### Reproduction

```vue
<template>
  <MyComponent
    static-prop="value1"
    another-prop="value2"
    v-bind="dynamicProps"
  />
</template>

<script setup>
const dynamicProps = { dynamicProp: 'dynamic' }
</script>
```

When the template is compiled, the static props don't get properly cleared from the properties array before merging with dynamic props. This causes unexpected behavior where properties might be duplicated or the merge doesn't work as expected.

### Expected behavior

Static props should be properly collected and merged with dynamic props without duplication. The compiled output should correctly merge all prop sources into a single props object.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

This seems to have started recently, possibly after a change to the props merging logic in the compiler.

---
Repository: /testbed
