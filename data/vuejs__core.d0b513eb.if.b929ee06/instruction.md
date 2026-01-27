# Bug Report

### Describe the bug

When using the `$on()` method with an array of event names, only the first event in the array is being registered. Subsequent events in the array are not properly bound to the handler function.

### Reproduction

```js
const vm = new Vue({
  // ...
})

// Register handler for multiple events
vm.$on(['event1', 'event2', 'event3'], () => {
  console.log('Handler called')
})

// Emit the events
vm.$emit('event1') // Works - logs "Handler called"
vm.$emit('event2') // Doesn't work - nothing happens
vm.$emit('event3') // Doesn't work - nothing happens
```

### Expected behavior

All events passed in the array should be registered with the same handler function. When any of the events are emitted, the handler should be called.

According to the documentation, `$on()` should accept either a string or an array of strings for the event parameter, and the handler should be registered for all events in the array.

### System Info
- Vue version: 3.x (compat mode)
- Environment: Node.js

---
Repository: /testbed
