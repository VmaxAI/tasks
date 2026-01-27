# Bug Report

### Describe the bug

I'm experiencing an issue with reactivity when using objects that have Symbol properties. When I watch an object that contains Symbol keys, the watcher doesn't seem to traverse the values associated with those Symbol properties correctly.

### Reproduction

```js
const symbolKey = Symbol('test')
const state = reactive({
  normalProp: { value: 1 },
  [symbolKey]: { value: 2 }
})

watch(
  () => state,
  () => {
    console.log('Changed!')
  },
  { deep: true }
)

// This triggers the watcher correctly
state.normalProp.value = 10

// This should trigger the watcher but doesn't work as expected
state[symbolKey].value = 20
```

### Expected behavior

When using deep watching, changes to nested properties accessed via Symbol keys should trigger the watcher callback, just like changes to regular string-keyed properties do.

### System Info
- Vue version: 3.x
- Node: 18.x

---
Repository: /testbed
