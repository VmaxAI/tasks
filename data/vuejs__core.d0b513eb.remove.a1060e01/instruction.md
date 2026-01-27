# Bug Report

### Describe the bug

I'm experiencing a critical issue where dynamically removing DOM elements from the page causes the application to crash. When trying to remove a child component or element, I get an error and the element is not properly removed from the DOM.

### Reproduction

```js
const app = createApp({
  template: `
    <div>
      <button @click="removeItem">Remove</button>
      <div v-if="show" ref="itemRef">Item to remove</div>
    </div>
  `,
  data() {
    return {
      show: true
    }
  },
  methods: {
    removeItem() {
      this.show = false
    }
  }
})
```

Steps to reproduce:
1. Create a component with a conditional element
2. Toggle the condition to remove the element
3. Application throws an error and the element remains in the DOM

### Expected behavior

The element should be cleanly removed from the DOM without errors. The parent-child relationship should be properly handled during removal.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox
- OS: Any

This is blocking our production deployment. Any help would be appreciated!

---
Repository: /testbed
