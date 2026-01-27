# Bug Report

### Describe the bug

I'm experiencing an issue with the event emitter when trying to register multiple event listeners at once using an array. When I pass an array of event names to `$on()`, the events don't seem to be registered correctly and the listeners never get called.

### Reproduction

```js
const vm = new Vue({
  // ...
})

// Trying to listen to multiple events at once
vm.$on(['eventA', 'eventB'], () => {
  console.log('Event triggered')
})

// Emitting the events
vm.$emit('eventA')  // Nothing happens
vm.$emit('eventB')  // Nothing happens
```

When I register the events individually, they work fine:

```js
vm.$on('eventA', () => {
  console.log('Event A triggered')
})

vm.$on('eventB', () => {
  console.log('Event B triggered')
})

vm.$emit('eventA')  // Works correctly
vm.$emit('eventB')  // Works correctly
```

### Expected behavior

When passing an array of event names to `$on()`, all events in the array should be registered with the same callback function, and emitting any of those events should trigger the callback.

### System Info
- Vue version: 3.x (compat mode)
- Node version: 18.x

---
Repository: /testbed
