# Bug Report

### Describe the bug

I'm experiencing an issue with effect cleanup where dependencies aren't being properly managed. After making changes to reactive state, effects seem to either fire when they shouldn't or don't fire when they should. The dependency tracking appears to be broken.

### Reproduction

```js
const count = ref(0)
const doubled = computed(() => count.value * 2)

// Create an effect that depends on doubled
effect(() => {
  console.log('Effect run:', doubled.value)
})

// Update the count
count.value = 1
count.value = 2

// Effects are not behaving correctly - either running too many times
// or not running when expected
```

### Expected behavior

Effects should only run when their actual dependencies change, and old/stale dependencies should be properly cleaned up. The effect should run the appropriate number of times based on the reactive changes.

### System Info
- Vue version: 3.x
- Node: 18.x

This seems related to the dependency cleanup logic - wondering if there was a recent change that might have affected this?

---
Repository: /testbed
