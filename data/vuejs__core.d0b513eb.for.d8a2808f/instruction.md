# Bug Report

### Describe the bug

First child element in a list is not rendering when mounting multiple children. When I have an array of child components or elements, the first one is consistently missing from the DOM while all subsequent children render correctly.

### Reproduction

```js
const App = {
  setup() {
    return () => h('div', [
      h('span', 'First'),
      h('span', 'Second'),
      h('span', 'Third')
    ])
  }
}
```

Expected to see three spans in the DOM, but only "Second" and "Third" are rendered. The first child is completely skipped.

This also happens with v-for:
```vue
<template>
  <div>
    <span v-for="item in items" :key="item">{{ item }}</span>
  </div>
</template>

<script setup>
const items = ['A', 'B', 'C']
</script>
```

Only 'B' and 'C' appear in the output.

### Expected behavior

All children should be rendered, including the first element in the array.

### System Info
- Vue version: 3.x
- Node: v18.x

---
Repository: /testbed
