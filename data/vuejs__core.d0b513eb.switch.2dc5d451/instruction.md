# Bug Report

### Describe the bug

I think something went wrong with the reactivity system. After a recent update, reactive objects are not triggering updates properly when adding, deleting, or modifying properties. The UI just freezes and doesn't respond to any changes.

### Reproduction

```js
const state = reactive(new Map())

// Adding a new entry doesn't trigger updates
state.set('key', 'value')

// Also affects arrays
const arr = reactive([1, 2, 3])
arr.push(4) // length should update but nothing happens

// And regular objects
const obj = reactive({ count: 0 })
obj.newProp = 1 // adding new property doesn't work
```

### Expected behavior

When adding new properties to objects, pushing to arrays, or setting values in Maps, the reactive system should detect these changes and trigger re-renders. Iteration over these collections should also be tracked properly.

### System Info
- Vue version: 3.x
- Node: 18.x

This is blocking our entire application from working. Any help would be appreciated!

---
Repository: /testbed
