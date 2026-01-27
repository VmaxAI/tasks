# Bug Report

### Describe the bug

When unmounting a Suspense component, the component appears to still be mounted internally even though it has been removed from the DOM. This causes issues when trying to check the mount state of Suspense components, especially in scenarios involving conditional rendering or dynamic component switching.

### Reproduction

```js
const app = createApp({
  template: `
    <Suspense v-if="show">
      <template #default>
        <AsyncComponent />
      </template>
    </Suspense>
  `,
  data() {
    return { show: true }
  }
})

// Mount the component
app.mount('#app')

// Unmount the Suspense
app.show = false

// The Suspense internal state incorrectly shows as not unmounted
// This can cause memory leaks or unexpected behavior when remounting
```

### Expected behavior

After unmounting a Suspense component, its internal `isUnmounted` flag should be set to `true` to properly reflect its unmounted state. This is important for cleanup operations and preventing memory leaks.

### System Info

- Vue version: 3.x
- Node version: 18.x

---
Repository: /testbed
