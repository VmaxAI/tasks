# Bug Report

### Describe the bug

After a recent update, I'm getting a runtime error when trying to use `hasOwnProperty` on reactive objects. The error says something like `hasOwnProperty is not a function` or similar.

### Reproduction

```js
const state = reactive({
  name: 'test',
  age: 25
})

// This throws an error
if (state.hasOwnProperty('name')) {
  console.log('has name property')
}
```

Also happens when checking properties dynamically:

```js
const key = 'age'
const exists = state.hasOwnProperty(key) // Error here
```

### Expected behavior

`hasOwnProperty` should work normally on reactive objects and return `true` or `false` based on whether the property exists on the object.

### System Info
- Vue version: 3.x
- Node: 18.x

---
Repository: /testbed
