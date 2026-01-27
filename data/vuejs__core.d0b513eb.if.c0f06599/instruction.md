# Bug Report

### Describe the bug

When using Vue 3's compatibility build with multiple app instances, the legacy APIs and compatibility mount methods are not being installed correctly. It appears that the singleton app instance is preventing the installation of these compatibility features on subsequent app instances.

### Reproduction

```js
import { createApp } from 'vue'
import { configureCompat } from '@vue/compat'

// Configure compat mode
configureCompat({
  MODE: 2
})

// Create first app instance
const app1 = createApp({
  template: '<div>App 1</div>'
})

// Create second app instance
const app2 = createApp({
  template: '<div>App 2</div>'
})

// Try to use legacy APIs on the second instance
// These APIs are not available even though compat mode is enabled
```

### Expected behavior

All app instances created in compatibility mode should have the legacy APIs and compatibility mount methods installed, not just the singleton app instance. Each app should be able to use Vue 2 style APIs when compat mode is enabled.

### System Info
- Vue version: 3.x (compat build)
- Node version: 18.x

---
Repository: /testbed
