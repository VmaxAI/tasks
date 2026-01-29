# Bug Report

### Describe the bug

The `.self` event modifier is not working correctly when handling events. It seems to be filtering events incorrectly based on the target element.

### Reproduction

```vue
<template>
  <div @click.self="handleClick">
    <button>Click me</button>
  </div>
</template>

<script setup>
const handleClick = () => {
  console.log('Div clicked')
}
</script>
```

### Expected behavior

The `handleClick` function should only be called when clicking directly on the `div` element itself, not when clicking on the `button` child element. Currently, the behavior is inconsistent and the handler may not be triggered even when clicking directly on the div.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox

---
Repository: /testbed
