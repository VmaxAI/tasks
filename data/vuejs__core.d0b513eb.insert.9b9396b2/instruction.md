# Bug Report

### Describe the bug
When rendering components with conditional elements or using v-if/v-for directives, I'm getting a runtime error saying `parent is not a function`. The application crashes completely when trying to insert DOM nodes.

### Reproduction
```js
<template>
  <div>
    <span v-if="show">Hello</span>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const show = ref(true)
</script>
```

Toggling the `show` value or any similar DOM manipulation causes the app to throw an error. This seems to affect any component that dynamically adds/removes elements from the DOM.

### Expected behavior
Components should render normally and DOM nodes should be inserted without errors.

### System Info
- Vue version: 3.x
- Browser: Chrome latest

---
Repository: /testbed
