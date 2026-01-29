# Bug Report

### Describe the bug
I'm experiencing an issue where accessing `this.state` before it's been set causes unexpected behavior in component methods. When I try to read a property value and assign it to a global property before updating the local state, the global property ends up with the wrong value.

### Reproduction
```js
export const Custom = defineComponent({
  data() {
    return {
      state: 'idle'
    }
  },
  
  methods: {
    aMethod() {
      // Trying to save current state to global before updating
      this.$.appContext.config.globalProperties.state = this.state
      this.state = 'running'
    }
  }
})
```

### Expected behavior
The global property should receive the current value of `this.state` (e.g., 'idle') before the local state is updated to 'running'. Instead, it seems like the assignment order is not being respected or the value isn't being captured correctly.

### System Info
- Vue version: 3.x

---
Repository: /testbed
