# Bug Report

### Describe the bug

I'm experiencing a syntax error in the compatibility layer code after a recent update. The application fails to load with a JavaScript parsing error related to the instance properties setup.

### Reproduction

When trying to use Vue 3 with compatibility mode enabled, the application crashes on initialization. This seems to be affecting the legacy helper functions that are used for Vue 2 compatibility.

```js
import { createApp } from 'vue'
import { configureCompat } from '@vue/compat'

configureCompat({
  MODE: 2
})

const app = createApp({
  template: '<div v-bind="attrs">test</div>',
  data() {
    return {
      attrs: { class: 'foo', id: 'bar' }
    }
  }
})

// App fails to mount due to syntax error
app.mount('#app')
```

### Expected behavior

The compatibility layer should work correctly and allow Vue 2 style code to run without syntax errors. The `v-bind` object syntax should properly bind all properties from the source object to the target element.

### System Info
- Vue version: 3.x (compat mode)
- Browser: Chrome/Firefox (any)
- Build tool: Vite/Webpack

The error appears to be in the runtime-core compatibility instance file where the legacy bind object props helper is defined.

---
Repository: /testbed
