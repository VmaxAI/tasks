# Bug Report

### Describe the bug

When using the Vue 2 compatibility mode event emitter with hook events (like `hook:mounted`), the deprecation warnings are being triggered incorrectly. Both the general `INSTANCE_EVENT_EMITTER` and `INSTANCE_EVENT_HOOKS` warnings appear for hook events, even though only the hook-specific warning should be shown.

### Reproduction

```js
// In Vue 3 with compat mode enabled
const instance = getCurrentInstance()

// This triggers both deprecation warnings instead of just INSTANCE_EVENT_HOOKS
instance.$on('hook:mounted', () => {
  console.log('mounted')
})
```

### Expected behavior

When registering a listener for a hook event (e.g., `hook:mounted`), only the `INSTANCE_EVENT_HOOKS` deprecation warning should be triggered. Regular events should trigger the `INSTANCE_EVENT_EMITTER` warning, but hook events should not trigger both warnings.

### System Info
- Vue version: 3.x (compat mode)
- Using migration build from Vue 2

---
Repository: /testbed
