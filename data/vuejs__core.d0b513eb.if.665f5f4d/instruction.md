# Bug Report

### Describe the bug

After a recent update, reactive objects are no longer triggering updates when properties are modified. When I set a value on a reactive object, the UI doesn't update and the change doesn't propagate to components watching that property.

### Reproduction

```js
const state = reactive({
  count: 0,
  user: {
    name: 'John'
  }
})

// This should trigger reactivity but nothing happens
state.count = 5

// Same issue with nested properties
state.user.name = 'Jane'

// Components watching these values don't re-render
```

### Expected behavior

When setting properties on a reactive object, the changes should be tracked and any components or effects depending on those properties should re-run/re-render automatically.

### Additional context

This was working fine in the previous version. The reactive object is created correctly and reading values works, but any modifications (SET operations) are completely ignored. It's like the trigger mechanism for property changes is broken.

### System Info
- Vue version: 3.x
- Environment: Development build

---
Repository: /testbed
