# Bug Report

### Describe the bug

The `.shift` event modifier is not working correctly - it's preventing events when the shift key IS pressed instead of when it's NOT pressed. This is the opposite of the expected behavior.

### Reproduction

```vue
<template>
  <button @click.shift="handleClick">Click me with shift</button>
</template>

<script setup>
const handleClick = () => {
  console.log('Shift click detected!')
}
</script>
```

**Steps to reproduce:**
1. Create a button with `@click.shift` modifier
2. Click the button while holding the shift key
3. The handler doesn't fire (but it should)
4. Click without shift key
5. The handler fires (but it shouldn't)

### Expected behavior

The `.shift` modifier should only allow the event handler to fire when the shift key IS pressed during the event. Currently it's doing the opposite - it fires when shift is NOT pressed and blocks when shift IS pressed.

### System Info
- Vue version: 3.x
- Browser: All browsers

This seems like a logic error where the modifier is checking the inverse condition.

---
Repository: /testbed
