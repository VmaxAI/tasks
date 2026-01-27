# Bug Report

### Describe the bug

I'm experiencing an issue with the `@` directive shorthand in templates. When I use `@click` or other event listeners, they're being incorrectly parsed as slot directives instead of event handlers.

### Reproduction

```vue
<template>
  <button @click="handleClick">Click me</button>
</template>

<script setup>
const handleClick = () => {
  console.log('clicked')
}
</script>
```

The `@click` directive is being treated as a slot directive rather than an event listener (`v-on`). This causes the click handler to not work at all.

### Expected behavior

The `@` shorthand should be parsed as `v-on` directive for event handling, not as a slot directive. The button should respond to click events.

### System Info
- Vue version: 3.x
- Browser: Chrome 120

---
Repository: /testbed
