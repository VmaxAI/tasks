# Bug Report

### Describe the bug

I'm experiencing unexpected behavior when triggering events in the runtime-test environment. When an event has multiple listeners attached, it seems like an extra invocation is happening beyond the registered listeners. Additionally, when triggering events with no payload, single listeners are not being called at all.

### Reproduction

```js
const el = document.createElement('div')

// Case 1: Multiple listeners
const listener1 = vi.fn()
const listener2 = vi.fn()
el.addEventListener('click', listener1)
el.addEventListener('click', listener2)
triggerEvent(el, 'click')

// Expected: listener1 and listener2 each called once
// Actual: Both listeners called, but something extra happens

// Case 2: Single listener with no payload
const singleListener = vi.fn()
el.addEventListener('focus', singleListener)
triggerEvent(el, 'focus')

// Expected: singleListener called once
// Actual: singleListener not called at all
```

### Expected behavior

- When multiple listeners are registered for the same event, each listener should be invoked exactly once
- When a single listener is registered, it should be invoked regardless of whether a payload is provided

### System Info
- Vue version: 3.x
- Environment: runtime-test

---
Repository: /testbed
