# Bug Report

### Describe the bug

The `beforeEnter` hook in transitions is not being called during initial mount. When a component with a transition is first rendered, the enter transition hooks are not firing as expected.

### Reproduction

```vue
<template>
  <Transition
    @before-enter="onBeforeEnter"
    @enter="onEnter"
  >
    <div v-if="show">Content</div>
  </Transition>
</template>

<script setup>
import { ref } from 'vue'

const show = ref(true)

function onBeforeEnter(el) {
  console.log('beforeEnter called')
}

function onEnter(el, done) {
  console.log('enter called')
  done()
}
</script>
```

When the component mounts with `show` initially set to `true`, the `beforeEnter` hook is not being triggered. The element appears without any transition.

### Expected behavior

The `beforeEnter` hook should be called during the initial mount when the element is being inserted into the DOM. The transition should play even on first render.

### System Info
- Vue version: 3.x
- Browser: Chrome

---
Repository: /testbed
