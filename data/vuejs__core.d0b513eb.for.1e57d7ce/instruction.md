# Bug Report

### Describe the bug

When removing multiple child elements from the DOM, the first child is not being unmounted properly. This causes memory leaks and potential side effects as the component's cleanup logic (like `onBeforeUnmount` and `onUnmounted` hooks) is not triggered for the first element.

### Reproduction

```js
const Parent = {
  setup() {
    const items = ref([1, 2, 3, 4, 5])
    
    const removeAll = () => {
      items.value = []
    }
    
    return { items, removeAll }
  },
  template: `
    <div>
      <Child v-for="item in items" :key="item" :id="item" />
      <button @click="removeAll">Remove All</button>
    </div>
  `
}

const Child = {
  props: ['id'],
  setup(props) {
    onUnmounted(() => {
      console.log('Unmounted:', props.id)
    })
    return () => h('div', `Child ${props.id}`)
  }
}
```

### Expected behavior

When clicking "Remove All", all children should be unmounted and log messages should appear for all 5 items:
```
Unmounted: 1
Unmounted: 2
Unmounted: 3
Unmounted: 4
Unmounted: 5
```

### Actual behavior

The first child (item 1) is skipped and never gets unmounted. Only items 2-5 trigger their unmount hooks. This leaves the first component in memory and any cleanup logic it has (like event listeners, timers, etc.) continues running.

### System Info
- Vue version: 3.x
- Environment: All browsers

---
Repository: /testbed
