# Bug Report

### Describe the bug

I'm experiencing an issue with component inheritance where child components are not properly inheriting the `provides` object from their parent components. It seems like the inheritance chain is broken or reversed.

### Reproduction

```js
// Parent component
const Parent = {
  setup() {
    provide('theme', 'dark')
    provide('user', { name: 'John' })
  },
  template: '<Child />'
}

// Child component
const Child = {
  setup() {
    const theme = inject('theme')
    const user = inject('user')
    console.log(theme) // Expected: 'dark', but not working correctly
    console.log(user) // Expected: { name: 'John' }, but not working correctly
  }
}
```

When I try to inject values provided by a parent component, the child component can't access them. It looks like the `provides` object is not being set up correctly in the component instance.

Additionally, I noticed that component IDs seem to be getting mixed up too - sometimes getting undefined values when there should be valid parent IDs.

### Expected behavior

Child components should be able to inject values that were provided by their parent components through the normal provide/inject API. The `provides` object should properly inherit from the parent's provides object.

### System Info
- Vue version: 3.x
- Node version: 18.x

---
Repository: /testbed
