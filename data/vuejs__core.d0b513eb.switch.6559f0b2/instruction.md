# Bug Report

### Describe the bug

I'm experiencing a critical issue where reactive collections (Maps, Sets, and Arrays) stop triggering updates when items are added or deleted. The reactivity system seems completely broken for collection mutations.

### Reproduction

```js
const state = reactive({
  items: new Map()
})

// Adding a new entry doesn't trigger updates
state.items.set('key1', 'value1')

// Component doesn't re-render
```

Another example with arrays:

```js
const list = reactive([1, 2, 3])

// Adding new item doesn't trigger reactivity
list.push(4)

// Length property isn't being tracked
```

And with deleting from objects:

```js
const obj = reactive({ a: 1, b: 2 })

// Deletion doesn't trigger updates
delete obj.a

// UI still shows the deleted property
```

### Expected behavior

- Adding items to Maps/Sets should trigger effects that depend on iteration
- Pushing to arrays should trigger length watchers
- Deleting properties should trigger iteration-dependent effects
- All collection mutations should properly notify subscribers

### System Info

- Vue version: 3.x
- This seems to affect all reactive collections

This is blocking our production deployment. Any help would be appreciated!

---
Repository: /testbed
