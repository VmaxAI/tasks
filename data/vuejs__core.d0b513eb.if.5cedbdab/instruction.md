# Bug Report

### Describe the bug

I'm experiencing an issue where props that are removed from a component are not being properly cleaned up. When a prop exists in the old props but is removed in the new props, the old value persists on the element instead of being removed.

### Reproduction

```js
// Initial render with props
<MyComponent foo="bar" baz="qux" />

// Update to remove 'foo' prop
<MyComponent baz="qux" />

// Expected: 'foo' should be removed from the element
// Actual: 'foo' remains on the element with its old value
```

This affects any props that are removed during updates. The component continues to have the old prop values even though they're no longer being passed.

### Expected behavior

When a prop is removed from a component (present in oldProps but not in newProps), it should be properly cleaned up and removed from the element. The element should not retain old prop values after they've been removed from the component's prop list.

### System Info
- Vue version: 3.x
- Runtime: runtime-core

---
Repository: /testbed
