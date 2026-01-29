# Bug Report

### Describe the bug

I'm experiencing an issue with the event emitter in compatibility mode where event listeners registered with `$on` are not being called after the first registration. It seems like the event registry is being reset or overwritten unexpectedly.

### Reproduction

```js
const instance = getCurrentInstance()

// Register first event listener
instance.$on('custom-event', () => {
  console.log('First listener')
})

// Register second event listener  
instance.$on('custom-event', () => {
  console.log('Second listener')
})

// Emit the event
instance.$emit('custom-event')

// Expected: Both listeners should be called
// Actual: Only the second listener is called (or no listeners are called)
```

### Expected behavior

All registered event listeners should be preserved and called when the event is emitted. The event registry should accumulate listeners, not replace them.

### System Info
- Vue version: 3.x (compat mode)
- Migrating from Vue 2.x

---
Repository: /testbed
