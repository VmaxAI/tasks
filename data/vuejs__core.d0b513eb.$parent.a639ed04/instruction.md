# Bug Report

### Describe the bug

I'm experiencing strange behavior with the `$parent` property in component instances. When accessing `this.$parent` from a child component, it seems to skip a level in the component hierarchy and returns the grandparent component instead of the direct parent.

### Reproduction

```js
// Parent.vue
<template>
  <Child />
</template>

<script>
export default {
  name: 'Parent',
  data() {
    return { parentValue: 'I am parent' }
  }
}
</script>

// Child.vue
<script>
export default {
  name: 'Child',
  mounted() {
    console.log(this.$parent) // Expected: Parent component
    console.log(this.$parent.$options.name) // Expected: 'Parent', but getting something else
  }
}
</script>
```

### Expected behavior

`this.$parent` should reference the immediate parent component in the component tree. If I have a structure like `Grandparent > Parent > Child`, then:
- From Child, `this.$parent` should be Parent
- From Parent, `this.$parent` should be Grandparent

Currently it appears to be skipping levels incorrectly.

### System Info
- Vue version: 3.x
- Node version: 18.x

---
Repository: /testbed
