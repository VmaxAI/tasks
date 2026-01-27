# Bug Report

### Describe the bug

I'm experiencing an issue with the rest props proxy where accessing properties that have `undefined` values behaves differently than expected. When a prop value is `undefined`, it seems to be returning a frozen/immutable version instead of the actual value from the props object.

### Reproduction

```js
const MyComponent = defineComponent({
  props: {
    foo: String,
    bar: String
  },
  setup(props) {
    const { foo, ...rest } = props
    
    // When bar is undefined, accessing it through rest
    // returns a frozen value instead of the actual prop value
    console.log(rest.bar) // Expected: undefined from props
    
    // This causes issues when trying to use the rest props
    // in child components or when checking reactivity
  }
})
```

### Expected behavior

The rest proxy should return the actual value from the props object consistently, regardless of whether the value is `undefined` or not. All prop values should maintain the same behavior and reactivity characteristics.

### System Info
- Vue version: 3.x

This seems like it might be related to how the proxy getter handles undefined values. The behavior is inconsistent with how defined values are accessed.

---
Repository: /testbed
