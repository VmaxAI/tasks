# Bug Report

### Describe the bug

I'm experiencing an issue with SSR hydration when using fragments with comment nodes. After hydrating, the DOM structure seems incorrect and subsequent operations fail or behave unexpectedly.

When hydrating components that contain fragments, the hydration process appears to skip over or incorrectly handle the closing comment markers. This causes the hydrated vnode tree to be out of sync with the actual DOM.

### Reproduction

```js
// Server-side rendered HTML contains fragment comments like:
// <!--[-->content<!--]-->

// During client-side hydration:
const app = createSSRApp({
  template: `
    <div>
      <template v-if="show">
        <span>Item 1</span>
        <span>Item 2</span>
      </template>
    </div>
  `,
  data() {
    return { show: true }
  }
})

app.mount('#app')
```

After hydration completes, trying to update the component or interact with the hydrated nodes results in incorrect behavior. The fragment boundaries seem to be misidentified.

### Expected behavior

The hydration process should correctly identify and handle fragment comment boundaries, allowing the client-side vnode tree to properly match the server-rendered DOM structure.

### System Info
- Vue version: 3.x
- Environment: SSR with client-side hydration
- Browser: Chrome/Firefox

---
Repository: /testbed
