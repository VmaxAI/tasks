# Bug Report

### Describe the bug

When using `defineModel()` without a parent v-model binding, local updates to the model value are not being reflected in the component. The setter appears to be checking for the presence of v-model props, but the logic seems inverted - it only updates the local value when a parent v-model exists, which prevents standalone usage of `defineModel()`.

### Reproduction

```vue
<script setup>
const model = defineModel()

// This update doesn't work when the component is used without v-model
function updateValue() {
  model.value = 'new value'
  console.log(model.value) // Still shows old value
}
</script>

<template>
  <div>
    <p>{{ model }}</p>
    <button @click="updateValue">Update</button>
  </div>
</template>
```

When using the component without v-model:
```vue
<MyComponent :modelValue="'initial'" />
```

The local state doesn't update when calling `model.value = 'new value'`.

### Expected behavior

`defineModel()` should allow local updates to the model value even when the component is not bound with v-model from the parent. The local state should update and trigger re-renders accordingly.

### System Info
- Vue version: 3.4+
- Using `defineModel()` macro

---
Repository: /testbed
