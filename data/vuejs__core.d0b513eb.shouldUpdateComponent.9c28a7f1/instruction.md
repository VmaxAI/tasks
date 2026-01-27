# Bug Report

### Describe the bug

Component updates are not being triggered correctly when dynamic props change. I'm experiencing an issue where the first dynamic prop in a component is being ignored during change detection, causing the component to not re-render when only that prop changes.

### Reproduction

```js
const DynamicComponent = {
  props: ['id', 'name', 'status'],
  template: '<div>{{ id }} - {{ name }} - {{ status }}</div>'
}

// Render with dynamic props
const vnode = h(DynamicComponent, {
  id: 1,
  name: 'test',
  status: 'active'
})

// Update only the first dynamic prop (id)
const updatedVnode = h(DynamicComponent, {
  id: 2,  // This change is not detected
  name: 'test',
  status: 'active'
})
```

When updating the component, changes to the first dynamic prop are not being detected, so the component doesn't update. However, if I change the second or third prop along with the first one, the update works correctly.

### Expected behavior

All dynamic props should be checked for changes, including the first one. The component should update whenever any dynamic prop changes, regardless of its position in the props array.

### Additional context

This seems to affect manually written render functions with dynamic props. The issue appears when only the first prop in the dynamic props list changes while others remain the same.

---
Repository: /testbed
