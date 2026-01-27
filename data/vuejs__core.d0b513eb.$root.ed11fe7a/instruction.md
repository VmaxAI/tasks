# Bug Report

### Describe the bug

I'm experiencing an issue with accessing `$root` in my Vue 3 application. When I try to access `$root` from a component instance, I'm getting an error instead of the expected root component instance.

### Reproduction

```js
// In a child component
export default {
  mounted() {
    console.log(this.$root) // Throws an error
    
    // Trying to access root component properties
    const rootData = this.$root.someProperty // Error occurs here
  }
}
```

The error seems to occur whenever I try to access `$root` from any component in the hierarchy. This is blocking me from accessing shared state or methods defined on the root component.

### Expected behavior

`this.$root` should return the root component instance, allowing access to its properties and methods. This worked fine in previous versions and is documented behavior.

### System Info
- Vue version: 3.x
- Node version: 18.x

Has anyone else run into this? Any workarounds would be appreciated!

---
Repository: /testbed
