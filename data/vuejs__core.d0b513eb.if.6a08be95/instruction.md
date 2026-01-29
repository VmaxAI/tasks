# Bug Report

### Describe the bug

I'm experiencing an issue with the `.sync` modifier in Vue 2 compatibility mode. When using `v-bind` with an object that includes the `.sync` modifier, the two-way binding is being set up even when it shouldn't be.

### Reproduction

```js
<template>
  <child-component v-bind.sync="props" />
</template>

<script>
export default {
  data() {
    return {
      props: {
        title: 'Hello',
        count: 0
      }
    }
  }
}
</script>
```

When the child component emits `update:title` or `update:count`, the parent's data is being updated even though `.sync` is specified. According to the docs, `.sync` should enable two-way binding, but it seems like the behavior is inverted - properties are getting update listeners when they shouldn't.

### Expected behavior

With `v-bind.sync`, the properties should have update listeners attached so changes from the child component propagate back to the parent. Without `.sync`, no update listeners should be created.

### System Info
- Vue version: 3.x (compat mode)
- Build: ESM bundler

This is blocking our migration from Vue 2 as we rely heavily on the `.sync` modifier for component communication. Any help would be appreciated!

---
Repository: /testbed
