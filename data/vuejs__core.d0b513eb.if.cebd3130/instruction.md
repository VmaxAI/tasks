# Bug Report

### Describe the bug

When using the `<Transition>` component, props that aren't part of the DOM transition validators (like custom event handlers or other component props) are no longer being passed through to the base transition props. This breaks functionality where you need to pass additional props to the transition component.

### Reproduction

```vue
<template>
  <Transition
    name="fade"
    @before-enter="handleBeforeEnter"
    :custom-data="someData"
  >
    <div v-if="show">Content</div>
  </Transition>
</template>

<script setup>
const show = ref(true)
const someData = ref({ value: 'test' })

function handleBeforeEnter(el) {
  console.log('before enter')
}
</script>
```

### Expected behavior

Custom props and event handlers that are not part of the standard DOM transition props should be passed through to the base transition component. The `@before-enter` hook should fire and `custom-data` should be accessible.

### Actual behavior

Custom props are not being forwarded, event handlers don't trigger, and the transition component only receives the standard DOM transition validator props.

### System Info
- Vue version: 3.x
- Runtime: DOM

This seems like a regression as this was working in previous versions.

---
Repository: /testbed
