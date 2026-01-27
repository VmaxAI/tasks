# Bug Report

### Describe the bug

I'm encountering an issue with the `$root` property in Vue 3 components. When accessing `this.$root` from a component, it seems to be returning the wrong component instance instead of the actual root component.

### Reproduction

```js
// Root component
const Root = {
  name: 'Root',
  template: '<Child />'
}

// Child component
const Child = {
  name: 'Child',
  mounted() {
    console.log(this.$root) // Expected: Root instance
    console.log(this.$root.name) // Should be 'Root' but gets something else
  }
}
```

### Expected behavior

`this.$root` should always return the root component instance of the application, not the current component instance. In the example above, accessing `this.$root` from the Child component should give me the Root component instance.

### System Info
- Vue version: 3.x

---
Repository: /testbed
