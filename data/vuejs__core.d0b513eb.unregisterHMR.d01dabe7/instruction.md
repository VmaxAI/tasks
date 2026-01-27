# Bug Report

### Describe the bug

I'm encountering an issue where component unmounting is not working correctly. When a component is unmounted, it appears that the lifecycle hooks are being called but the component cleanup isn't happening properly. The component seems to remain in a partially mounted state even after unmounting.

### Reproduction

```js
const app = createApp({
  setup() {
    const show = ref(true)
    
    onMounted(() => {
      console.log('Parent mounted')
    })
    
    return { show }
  },
  template: `
    <div>
      <ChildComponent v-if="show" />
      <button @click="show = false">Unmount</button>
    </div>
  `
})

const ChildComponent = {
  setup() {
    onBeforeUnmount(() => {
      console.log('beforeUnmount called')
    })
    
    onUnmounted(() => {
      console.log('unmounted called')
    })
  },
  template: '<div>Child</div>'
}
```

When clicking the unmount button, the hooks fire but the component doesn't fully clean up. This causes issues with:
- Component state not being properly cleared
- Watchers and effects still running
- Memory leaks in long-running applications

### Expected behavior

The component should be completely unmounted and cleaned up when removed from the DOM. All lifecycle hooks should execute and the component instance should be properly disposed.

### System Info
- Vue version: 3.x
- Build: Development mode

---
Repository: /testbed
