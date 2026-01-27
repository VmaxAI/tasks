# Bug Report

### Describe the bug

I'm experiencing an issue with reactive arrays where changes to array elements at numeric indices are not triggering proper reactivity updates. When I modify an array element by index, components that iterate over the array don't re-render as expected.

### Reproduction

```js
const state = reactive({
  items: [1, 2, 3, 4, 5]
})

// Modify an element by index
state.items[2] = 99

// Components using v-for over state.items don't update
```

The array modification happens successfully (the value is changed), but any components that are iterating over the array using `v-for` or similar patterns don't reflect the change in the UI.

### Expected behavior

When modifying an array element by its numeric index, components that iterate over that array should automatically re-render to reflect the change.

### System Info
- Vue version: 3.x
- Node version: 18.x

This seems to have broken recently, as it was working fine before. Any help would be appreciated!

---
Repository: /testbed
