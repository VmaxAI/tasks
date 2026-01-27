# Bug Report

### Describe the bug

I'm having an issue with the `inject` option when using array syntax. It seems like the first item in the inject array is being ignored and not properly registered for injection.

### Reproduction

```js
export default {
  inject: ['store', 'theme', 'config'],
  mounted() {
    console.log(this.store) // undefined - first item not injected!
    console.log(this.theme) // works
    console.log(this.config) // works
  }
}
```

When I provide an array of injection keys, only the items after the first one are actually available in the component. The first key in the array returns `undefined` even though it's provided by a parent component.

### Expected behavior

All items in the inject array should be properly injected into the component, including the first one. The array syntax should treat all elements equally.

### System Info
- Vue version: 3.x

This is blocking our migration as we have many components using array-style inject declarations. Any help would be appreciated!

---
Repository: /testbed
