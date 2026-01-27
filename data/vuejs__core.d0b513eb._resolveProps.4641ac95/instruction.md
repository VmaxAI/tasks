# Bug Report

### Describe the bug

Custom elements created with `defineCustomElement` are not properly recognizing props that are set before the component is connected to the DOM. When setting props on a custom element instance before it's mounted, those initial values are being ignored.

### Reproduction

```js
import { defineCustomElement } from 'vue'

const MyElement = defineCustomElement({
  props: {
    message: String,
    count: Number
  },
  template: `<div>{{ message }} - {{ count }}</div>`
})

customElements.define('my-element', MyElement)

// Create element and set props before connecting
const el = document.createElement('my-element')
el.message = 'Hello'
el.count = 42

// Props are not recognized after mounting
document.body.appendChild(el)
// Expected: "Hello - 42"
// Actual: " - " (empty values)
```

### Expected behavior

Props set on the custom element instance before it's connected to the DOM should be properly initialized and available when the component mounts.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox

This seems to affect any props set programmatically before the element is added to the document. Props set via attributes or after mounting work fine, but pre-mount property assignment doesn't work anymore.

---
Repository: /testbed
