# Bug Report

### Describe the bug

The `errorCaptured` hook is not working as expected. When multiple error handlers are registered, the error propagation logic seems to be inverted. Errors are being suppressed when they should propagate, and vice versa.

### Reproduction

```js
const Parent = {
  errorCaptured(err) {
    console.log('Parent caught error')
    return false // Should stop propagation
  },
  render() {
    return h(Child)
  }
}

const Child = {
  errorCaptured(err) {
    console.log('Child caught error')
    return true // Should allow propagation
  },
  setup() {
    throw new Error('Test error')
  }
}
```

### Expected behavior

According to the docs, `errorCaptured` should:
- Stop propagation when returning `false`
- Continue propagation when returning `true` or `undefined`

Currently, the behavior seems reversed - errors are being stopped when they should continue, and continuing when they should be stopped.

### System Info
- Vue version: 3.x
- Node version: 18.x

---
Repository: /testbed
