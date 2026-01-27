# Bug Report

### Describe the bug
After a recent update, reactive collections (Maps, Sets, Arrays) are not triggering updates properly when elements are added or removed. The reactivity system seems to have stopped working for collection mutations.

### Reproduction
```js
const map = reactive(new Map())
const arr = reactive([1, 2, 3])

// These changes don't trigger reactivity
map.set('key', 'value')
arr.push(4)
arr.splice(0, 1)

// Also affects iteration - watchers on collections don't fire
watch(() => [...map.keys()], () => {
  console.log('Map changed') // Never called
})
```

### Expected behavior
- Adding items to reactive Maps should trigger effects that depend on the Map
- Array mutations (push, splice, etc.) should trigger length watchers and iteration effects
- Deleting items from reactive collections should trigger dependent effects
- Iteration over reactive collections should be tracked properly

### System Info
- Vue version: 3.x
- Environment: Node.js

The trigger logic for ADD/DELETE/SET operations on collections appears to be completely broken. None of my computed properties or watchers that depend on reactive collections are updating anymore.

---
Repository: /testbed
