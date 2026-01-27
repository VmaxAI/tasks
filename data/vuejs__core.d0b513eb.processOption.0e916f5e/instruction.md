# Bug Report

### Describe the bug

I'm experiencing an issue with v-model on `<select>` elements in SSR mode. When I have a select with options inside an optgroup, the selected attribute is not being applied correctly to the options during server-side rendering.

### Reproduction

```vue
<template>
  <select v-model="selectedValue">
    <optgroup label="Group 1">
      <option value="a">Option A</option>
      <option value="b">Option B</option>
    </optgroup>
  </select>
</template>

<script setup>
const selectedValue = ref('b')
</script>
```

When rendering this on the server with `selectedValue` set to `'b'`, the second option should have the `selected` attribute, but it doesn't appear in the rendered HTML.

### Expected behavior

The option matching the v-model value should have the `selected` attribute in the SSR output, even when nested inside an `<optgroup>`. 

For example, if `selectedValue` is `'b'`, the rendered HTML should include:
```html
<option value="b" selected>Option B</option>
```

### System Info
- Vue version: 3.x
- SSR mode

This seems to only affect options inside optgroups. Options that are direct children of the select work fine.

---
Repository: /testbed
