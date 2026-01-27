# Bug Report

### Describe the bug

I'm experiencing an issue with reactivity when using objects that have Symbol properties. When watching an object that contains Symbol keys, changes to the values associated with those Symbol properties are not being tracked properly.

### Reproduction

```js
const symbolKey = Symbol('mySymbol')

const state = reactive({
  normalProp: 'test',
  [symbolKey]: { nested: 'value' }
})

watch(
  () => state,
  () => {
    console.log('State changed')
  },
  { deep: true }
)

// This change is not detected
state[symbolKey].nested = 'updated'
```

### Expected behavior

When modifying nested properties of Symbol-keyed values, the watcher should trigger and detect the change. Currently, the reactivity system doesn't seem to be traversing into the actual values of Symbol properties during deep watching.

### System Info
- Vue version: 3.x
- Node version: 18.x

---
Repository: /testbed
