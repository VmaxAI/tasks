# Bug Report

### Describe the bug

After a recent update, the reactivity system seems to be completely broken. When I try to add, delete, or modify properties on reactive objects, the changes aren't being tracked at all and nothing updates.

### Reproduction

```js
const state = reactive({
  items: []
})

// Adding new items doesn't trigger updates
state.items.push({ id: 1, name: 'Item 1' })

// Also tried with objects
const obj = reactive({
  count: 0
})

obj.newProp = 'test' // No reactivity triggered
delete obj.count // No reactivity triggered

// Even Map operations don't work
const map = reactive(new Map())
map.set('key', 'value') // No updates
```

### Expected behavior

- Adding new properties should trigger reactivity for iteration-based watchers
- Deleting properties should trigger reactivity updates
- Map operations (set, delete) should properly notify subscribers
- Array operations that change length should trigger length watchers

### System Info

- Vue version: 3.x
- Browser: Chrome/Firefox (happens in both)

This is a critical issue as it breaks the core reactivity system. Any help would be appreciated!

---
Repository: /testbed
