# Bug Report

### Describe the bug

I'm experiencing an issue with the `.alt` event modifier. When I use `@click.alt` on an element, the click handler is being triggered even when the Alt key is NOT pressed. This seems like the opposite of what should happen.

### Reproduction

```vue
<template>
  <button @click.alt="handleAltClick">Click me with Alt</button>
</template>

<script setup>
const handleAltClick = () => {
  console.log('Alt+Click detected!')
}
</script>
```

**Steps to reproduce:**
1. Click the button WITHOUT holding the Alt key
2. The handler fires (it shouldn't)
3. Click the button WITH the Alt key held down
4. The handler also fires (this is correct)

### Expected behavior

The click handler should ONLY fire when the Alt key is pressed during the click. Regular clicks without Alt should be ignored.

### System Info
- Vue version: 3.x
- Browser: Firefox 121

This is affecting keyboard shortcuts in my app. Other modifiers like `.ctrl` and `.shift` seem to work fine, just `.alt` is behaving incorrectly.

---
Repository: /testbed
