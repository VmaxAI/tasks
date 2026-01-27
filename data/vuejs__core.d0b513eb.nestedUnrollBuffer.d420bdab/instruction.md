# Bug Report

### Describe the bug

I'm experiencing an infinite loop/hang when using server-side rendering with nested async components. The server appears to get stuck and never completes the rendering process.

### Reproduction

```js
import { createSSRApp } from 'vue'
import { renderToString } from 'vue/server-renderer'

const AsyncChild = defineAsyncComponent(() => 
  Promise.resolve({
    template: '<div>Async content</div>'
  })
)

const AsyncParent = defineAsyncComponent(() =>
  Promise.resolve({
    components: { AsyncChild },
    template: '<div><AsyncChild /></div>'
  })
)

const app = createSSRApp({
  components: { AsyncParent },
  template: '<AsyncParent />'
})

// This never resolves
await renderToString(app)
```

### Expected behavior

The `renderToString` should complete and return the rendered HTML string for the nested async components.

### System Info
- Vue version: 3.x
- Node: 18.x

The rendering just hangs indefinitely when there are async components nested within other async components. It seems like something is stuck in a loop during the buffer processing.

---
Repository: /testbed
