# Bug Report

### Describe the bug

I'm experiencing an issue with the Vue 3 compatibility build where the application fails to initialize properly. When trying to use `createApp` through the compat layer, it seems like the wrong factory function is being used, causing the app creation to fail.

### Reproduction

```js
import { createCompatVue } from '@vue/compat'

const Vue = createCompatVue()

// Trying to create an app instance
const app = Vue.createApp({
  data() {
    return {
      message: 'Hello'
    }
  }
})

app.mount('#app')
```

### Expected behavior

The app should be created successfully using the compatibility layer, with all Vue 3 runtime DOM functionality available on the Vue instance. The compat build should properly merge the createApp functionality with the runtime DOM APIs.

### System Info
- @vue/compat version: latest
- Node version: 18.x

The app creation seems to be using an incorrect configuration, possibly with arguments passed in the wrong order to the underlying compatibility utility. This prevents proper initialization of Vue applications through the compat build.

---
Repository: /testbed
