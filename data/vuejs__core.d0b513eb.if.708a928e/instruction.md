# Bug Report

### Describe the bug

After unmounting an app, the container element still references the Vue app instance. When trying to mount a new app on the same container, it causes unexpected behavior because the old app reference isn't properly cleaned up.

### Reproduction

```js
const container = document.getElementById('app')

// Mount first app
const app1 = createApp(Component1)
app1.mount(container)

// Unmount
app1.unmount()

// Try to mount a new app on the same container
const app2 = createApp(Component2)
app2.mount(container) // This doesn't work as expected
```

### Expected behavior

After calling `unmount()`, the container should be completely cleaned up and ready to accept a new Vue app. The `__vue_app__` property should be removed from the container element before the render call, allowing a fresh mount.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox

---
Repository: /testbed
