# Bug Report

### Describe the bug

After a recent update, I'm getting unexpected errors when using `hasOwnProperty` on reactive objects. The method seems to have been completely removed or replaced with something unrelated, causing runtime errors in my application.

### Reproduction

```js
const state = reactive({
  name: 'test',
  age: 25
})

// This throws an error now
const hasName = state.hasOwnProperty('name')
console.log(hasName) // Expected: true
```

The `hasOwnProperty` method is no longer working on reactive objects. When I try to check if a property exists using this method, I get errors about the function not being defined or not working as expected.

### Expected behavior

The `hasOwnProperty` method should work correctly on reactive objects and return `true` when the property exists and `false` when it doesn't. This is standard JavaScript behavior that should be preserved even for proxied objects.

### System Info

- Vue version: 3.x
- Node: 18.x

This is breaking existing code that relies on checking property existence using `hasOwnProperty`. Any help would be appreciated!

---
Repository: /testbed
