# Bug Report

### Describe the bug

Scoped styles are not being applied correctly to component root elements. The scope ID attribute appears to be missing or incorrectly set on elements, causing styles to not match their intended targets.

### Reproduction

```vue
<!-- Parent.vue -->
<template>
  <div>
    <Child />
  </div>
</template>

<style scoped>
.child-root {
  color: red;
}
</style>

<!-- Child.vue -->
<template>
  <div class="child-root">
    This should be red
  </div>
</template>
```

When rendering the child component, the scoped style from the parent doesn't apply as expected. The scope ID attributes on the elements don't seem to be set up properly.

### Expected behavior

The child component's root element should inherit the parent's scope ID and the scoped styles should apply correctly.

### System Info

- Vue version: 3.x
- Environment: Browser

---
Repository: /testbed
