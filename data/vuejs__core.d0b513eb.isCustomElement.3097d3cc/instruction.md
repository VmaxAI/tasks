# Bug Report

### Describe the bug

When configuring `ignoredElements` in Vue 2 compatibility mode, custom elements are not being properly recognized. Elements that should be treated as custom elements are instead being treated as unknown components, causing warnings in the console.

### Reproduction

```js
import { createApp, configureCompat } from 'vue'

configureCompat({
  MODE: 2
})

const app = createApp({
  template: '<my-custom-element></my-custom-element>'
})

// Configure ignoredElements like in Vue 2
app.config.ignoredElements = ['my-custom-element']

app.mount('#app')
```

### Expected behavior

The custom element `<my-custom-element>` should be recognized and not produce any warnings, just like it worked in Vue 2 with `ignoredElements`.

### Actual behavior

Getting warnings about unknown custom elements even though they're listed in `ignoredElements`. The elements that should be ignored are still triggering component resolution warnings.

### System Info
- Vue version: 3.x (compat mode)
- Browser: Chrome

This is blocking migration from Vue 2 as we have several custom web components that need to be properly ignored.

---
Repository: /testbed
