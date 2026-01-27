# Bug Report

### Describe the bug

Dynamic directive arguments with square brackets are not being parsed correctly. When using directives like `v-on:[eventName]` or `v-bind:[propName]`, the closing bracket `]` is not properly recognized, causing the parser to treat the rest of the template incorrectly.

### Reproduction

```vue
<template>
  <div v-on:[dynamicEvent]="handler">Click me</div>
</template>

<script>
export default {
  data() {
    return {
      dynamicEvent: 'click'
    }
  },
  methods: {
    handler() {
      console.log('clicked')
    }
  }
}
</script>
```

The template fails to compile or behaves unexpectedly. The dynamic argument syntax with brackets doesn't work as expected.

### Expected behavior

The template should compile correctly and the dynamic directive argument should be properly parsed. The closing `]` bracket should be recognized as the end of the dynamic argument expression.

### System Info
- Vue version: 3.x
- Node version: 18.x

---
Repository: /testbed
