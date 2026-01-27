# Bug Report

### Describe the bug

I'm getting incorrect warning messages when using `useHost()` in custom elements. The warning logic seems to be backwards - it's showing "called without an active component instance" when there IS an active instance, and showing "can only be used in components defined via defineCustomElement" when there ISN'T an instance.

### Reproduction

```js
import { defineCustomElement, useHost } from 'vue'

const MyElement = defineCustomElement({
  setup() {
    // This incorrectly warns about "called without an active component instance"
    // even though we're inside a valid component setup
    const host = useHost()
    return {}
  }
})

customElements.define('my-element', MyElement)
```

Also, if you try to call `useHost()` outside of any component context, you get the wrong warning message about it only being usable in defineCustomElement components instead of the "no active component instance" message.

### Expected behavior

The warnings should be:
- "called without an active component instance" → when there's NO instance
- "can only be used in components defined via defineCustomElement" → when there IS an instance but it's not a custom element

Currently it's showing these messages in the opposite situations.

### System Info
- Vue version: 3.x

---
Repository: /testbed
