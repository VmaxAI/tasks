# Bug Report

### Describe the bug

I'm experiencing an issue with mounting Vue applications in compatibility mode. When attempting to mount a root instance multiple times, the second mount operation succeeds instead of being prevented. This allows the same app to be mounted multiple times, which leads to unexpected behavior.

### Reproduction

```js
const app = createApp({
  template: '<div>Hello</div>'
})

// Mount the app for the first time
app.mount('#app')

// Try to mount again - this should be prevented but isn't
app.mount('#app')  // This succeeds when it shouldn't
```

### Expected behavior

The second `mount()` call should be prevented and a warning should be shown in development mode indicating that the root instance is already mounted. The app should only be mountable once.

### System Info
- Vue version: 3.x (compat mode)
- Environment: Browser

---
Repository: /testbed
