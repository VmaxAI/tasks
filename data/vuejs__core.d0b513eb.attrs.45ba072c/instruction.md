# Bug Report

### Describe the bug

When accessing `attrs` in the setup context during development mode, the attributes object is no longer read-only. This allows accidental mutations to `attrs` which should be immutable according to Vue's design principles.

### Reproduction

```js
export default {
  setup(props, { attrs }) {
    // This should not be allowed but currently works
    attrs.class = 'modified'
    attrs['data-test'] = 'new-value'
    
    console.log(attrs) // Shows mutated values
  }
}
```

### Expected behavior

The `attrs` object should be read-only in development mode to prevent accidental mutations. Attempting to modify `attrs` should either:
1. Throw an error in strict mode
2. Fail silently but not actually mutate the object

This is important because `attrs` represents fallthrough attributes that should be treated as immutable props.

### System Info
- Vue version: 3.x
- Environment: Development mode

---
Repository: /testbed
