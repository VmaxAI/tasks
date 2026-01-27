# Bug Report

### Describe the bug

After a recent update, I'm getting a runtime error when trying to use array methods on reactive arrays. It seems like the type guard function `isMutatingArrayMethod` is missing or broken, causing the array method handling to fail completely.

### Reproduction

```js
const state = reactive({
  items: [1, 2, 3, 4, 5]
})

// This throws an error
state.items.push(6)

// This also fails
state.items.splice(0, 1)
```

### Expected behavior

Array methods like `push`, `pop`, `splice`, etc. should work normally on reactive arrays without throwing errors. The reactivity system should be able to detect which methods mutate the array and trigger updates accordingly.

### Additional context

This appears to have broken in the latest version. The error suggests that the internal method detection logic is not working properly. All mutating array methods seem to be affected.

---
Repository: /testbed
