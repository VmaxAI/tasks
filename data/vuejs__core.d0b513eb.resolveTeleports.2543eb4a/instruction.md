# Bug Report

### Describe the bug

When using Teleport components with SSR (server-side rendering), the teleported content is not being rendered correctly. The teleport targets remain empty even though the content should be teleported to them.

### Reproduction

```vue
<template>
  <div>
    <Teleport to="#modal">
      <div>Modal content</div>
    </Teleport>
    <div id="modal"></div>
  </div>
</template>
```

When rendering this component on the server:

```js
import { renderToString } from '@vue/server-renderer'
import { createSSRApp } from 'vue'

const app = createSSRApp(MyComponent)
const html = await renderToString(app)

// Expected: html should contain the teleported content in #modal
// Actual: #modal div is empty, teleported content is missing
```

### Expected behavior

The teleported content should appear in the target element (`#modal`) in the server-rendered HTML output. The teleport functionality should work correctly during SSR just like it does in client-side rendering.

### System Info

- Vue version: 3.x
- Node.js version: 18.x
- Using server-renderer for SSR

This seems to have broken recently. The teleported content just disappears during server rendering.

---
Repository: /testbed
