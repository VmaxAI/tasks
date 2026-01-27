# Bug Report

### Describe the bug

When trying to mount a Vue app using a DOM element directly (not a selector string), the app fails to mount properly. It seems like the mounting logic is treating element objects as if they were selector strings, which causes `document.querySelector()` to be called with an invalid argument.

### Reproduction

```js
import { createApp } from 'vue'
import App from './App.vue'

// Get a reference to an actual DOM element
const container = document.getElementById('app')

// Try to mount using the element directly
createApp(App).mount(container)
```

The above code throws an error because it's trying to use `querySelector` on an element object instead of just using the element directly.

### Expected behavior

When passing a DOM element (not a string selector) to `mount()`, it should use that element directly as the mount target without trying to call `querySelector` on it. This used to work in previous versions.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox
- OS: Any

---
Repository: /testbed
