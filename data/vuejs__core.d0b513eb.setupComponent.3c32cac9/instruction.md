# Bug Report

### Describe the bug

I'm experiencing an issue with SSR setup state management. It appears that the SSR setup state flag is being incorrectly set/unset during component setup, which causes problems when components are being initialized in SSR mode.

### Reproduction

```js
// Setup a component in SSR context
const instance = {
  // component instance properties
}

// During setupComponent execution in SSR mode
setupComponent(instance, props, isStateful = true, isSSR = true)

// The SSR setup state flag gets set incorrectly
// This affects subsequent component initialization
```

### Expected behavior

The SSR setup state should be properly managed throughout the component setup lifecycle. The flag should be set and unset at the correct times to ensure proper SSR rendering behavior.

### System Info
- Vue version: 3.x
- Environment: SSR

---
Repository: /testbed
