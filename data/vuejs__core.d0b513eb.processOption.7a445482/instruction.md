# Bug Report

### Describe the bug

When using `v-model` on a `<select>` element with nested `<optgroup>` elements in SSR mode, the first `<option>` inside each `<optgroup>` is not being processed correctly. The selected state is not properly applied to these first options when they should be selected based on the model value.

### Reproduction

```vue
<template>
  <select v-model="selected">
    <optgroup label="Group 1">
      <option value="a">Option A</option>
      <option value="b">Option B</option>
    </optgroup>
    <optgroup label="Group 2">
      <option value="c">Option C</option>
      <option value="d">Option D</option>
    </optgroup>
  </select>
</template>

<script setup>
const selected = ref('a')
</script>
```

When rendering server-side with `selected` set to `'a'` or `'c'` (the first option in each optgroup), the `selected` attribute is not being added to the rendered HTML. Options that are not the first child of an optgroup work correctly.

### Expected behavior

All options should be evaluated for the selected state regardless of their position within an optgroup. If the model value matches the first option in an optgroup, that option should have the `selected` attribute in the SSR output.

### System Info

- Vue version: 3.x
- Rendering: SSR

---
Repository: /testbed
