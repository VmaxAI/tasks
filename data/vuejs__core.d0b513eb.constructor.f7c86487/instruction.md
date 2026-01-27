# Bug Report

### Describe the bug

I'm experiencing an issue with reactive objects where modifications to properties are not being tracked properly. It seems like the reactivity system is not detecting changes when I update values in my reactive state.

### Reproduction

```js
const state = reactive({
  count: 0,
  items: []
})

// Updating properties doesn't trigger reactivity
state.count = 10
state.items.push('new item')

// The component doesn't re-render even though the data changed
```

### Expected behavior

When modifying properties on a reactive object, the changes should be tracked and trigger updates. The component should re-render to reflect the new state.

### System Info
- Vue version: 3.x
- Node: 18.x

Has anyone else encountered this? This seems to have broken recently and I'm not sure what changed.

---
Repository: /testbed
