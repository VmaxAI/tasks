# Bug Report

### Describe the bug

When using Vue 3 compat mode with components that have a `modelValue` prop declared as an array, the deprecation warning for `COMPONENT_V_MODEL` is not being triggered correctly. The warning message should be shown when a component declares `modelValue` in its props array, but it's not detecting it properly.

### Reproduction

```js
const MyComponent = {
  props: ['modelValue', 'otherProp'],
  template: '<input :value="modelValue" @input="$emit(\'update:modelValue\', $event.target.value)">'
}

// Use the component with v-model in compat mode
// Expected: deprecation warning should be shown
// Actual: no warning is triggered
```

### Expected behavior

The compat mode should detect when a component declares `modelValue` in its props array and show the appropriate deprecation warning message indicating that the component is using Vue 3 syntax but running under Vue 2 compat v-model behavior.

### System Info
- Vue version: 3.x (compat mode)
- Using array-style props declaration

---
Repository: /testbed
