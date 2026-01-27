# Bug Report

### Describe the bug

I'm encountering a strange issue where properties defined in `setup()` and `data()` seem to be returning the wrong values. When I access a property that exists in both `setup()` and `data()`, I'm getting the value from the wrong source.

### Reproduction

```js
export default {
  setup() {
    const message = ref('from setup')
    return {
      message
    }
  },
  data() {
    return {
      message: 'from data'
    }
  },
  mounted() {
    console.log(this.message) // Expected: 'from setup', but getting 'from data'
  }
}
```

### Expected behavior

According to the Vue 3 documentation, properties returned from `setup()` should take precedence over properties in `data()`. When accessing `this.message`, it should return the value from `setup()` ('from setup'), but instead it's returning the value from `data()` ('from data').

This is causing issues in my application where I'm migrating from Options API to Composition API and have some overlap between the two approaches during the transition.

### System Info
- Vue version: 3.x
- Node version: 18.x

---
Repository: /testbed
