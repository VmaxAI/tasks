# Bug Report

### Describe the bug

I'm experiencing an issue with accessing `_data` on component instances in compatibility mode. After a recent update, `_data` now returns an object with a `value` property instead of the actual data object directly.

### Reproduction

```js
export default {
  data() {
    return {
      message: 'Hello'
    }
  },
  mounted() {
    // This used to work
    console.log(this._data.message) // undefined
    
    // Now it seems to be wrapped
    console.log(this._data) // { value: { message: 'Hello' } }
  }
}
```

### Expected behavior

`this._data` should return the component's data object directly, not wrapped in a `{ value: ... }` structure. This is breaking existing code that relies on accessing `_data` for debugging or other purposes.

### System Info
- Vue version: 3.x (compat mode)
- Browser: Chrome

---
Repository: /testbed
