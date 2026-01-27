# Bug Report

### Describe the bug

When using `createSSRApp()` and mounting to a container, the app fails to mount properly. The mount operation returns `undefined` instead of the app instance, and the app doesn't render to the DOM.

### Reproduction

```js
import { createSSRApp } from 'vue'

const app = createSSRApp({
  template: '<div>Hello World</div>'
})

// This returns undefined and doesn't render
const result = app.mount('#app')
console.log(result) // undefined
```

### Expected behavior

The app should mount successfully to the container and return the component instance. The content should be rendered to the DOM.

### Additional context

This seems to happen specifically with `createSSRApp()`. Regular `createApp()` works fine. The container element exists in the DOM but nothing gets rendered into it.

---
Repository: /testbed
