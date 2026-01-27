# Bug Report

### Describe the bug

I'm experiencing an issue with watchers in SSR mode. When using `watch` or `watchEffect` with `flush: 'sync'`, the watcher cleanup is not being registered properly during server-side rendering. This causes memory leaks and potential issues with cleanup handlers not being called.

### Reproduction

```js
// In an SSR component setup
import { watch, ref } from 'vue'

const count = ref(0)

// This watcher's cleanup is not registered in SSR context
watch(count, (newVal) => {
  console.log('count changed:', newVal)
}, { flush: 'sync' })
```

### Expected behavior

Watchers with `flush: 'sync'` should have their cleanup handlers properly registered in the SSR context, similar to how `flush: 'post'` watchers are handled. The cleanup should be tracked in `ctx.__watcherHandles` to ensure proper cleanup during SSR.

### Additional context

This seems to affect specifically:
- Watchers with `flush: 'sync'` option
- Components running in SSR mode
- Cleanup registration in the SSR context

The issue doesn't occur with `flush: 'post'` watchers, which work as expected.

---
Repository: /testbed
