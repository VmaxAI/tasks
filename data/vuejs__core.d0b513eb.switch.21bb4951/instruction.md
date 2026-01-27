# Bug Report

### Describe the bug

I'm experiencing a critical issue where reactive collections (Maps, Sets, and Arrays) are not triggering updates properly when items are added or deleted. The reactivity system seems to have completely broken for these operations.

### Reproduction

```js
const state = reactive({
  items: new Map()
})

// Adding a new entry doesn't trigger updates
state.items.set('key1', 'value1')

// Component doesn't re-render
```

```js
const list = reactive([1, 2, 3])

// Adding new items doesn't trigger length watchers
list.push(4)

// No reactivity update occurs
```

```js
const obj = reactive({
  count: 0,
  data: {}
})

// Adding new properties doesn't trigger iteration
obj.data.newProp = 'test'

// Watchers on the object don't fire
```

### Expected behavior

- When adding items to a Map, components that iterate over the Map should re-render
- When pushing to an array, watchers on the array length should trigger
- When adding/deleting properties from objects, iteration-based watchers should update
- Map.SET operations should trigger ITERATE_KEY dependencies

### System Info

This appears to affect all reactive collections after a recent update. The trigger mechanism for ADD/DELETE/SET operations seems to not be working at all.

---
Repository: /testbed
