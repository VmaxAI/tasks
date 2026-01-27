# Bug Report

### Describe the bug

When using `renderToSimpleStream()` with a raw VNode, the rendering doesn't work as expected. The stream output appears to be incorrect or empty instead of rendering the VNode content properly.

### Reproduction

```js
import { h } from 'vue'
import { renderToSimpleStream } from '@vue/server-renderer'

const vnode = h('div', { class: 'test' }, 'Hello World')

// Try to render a raw vnode directly
const stream = renderToSimpleStream(vnode, {})

// The output is not what's expected
```

### Expected behavior

When passing a raw VNode to `renderToSimpleStream()`, it should render the VNode content correctly to the stream output, just like when passing a full app instance.

### System Info
- Vue version: 3.x
- Environment: Node.js SSR

---
Repository: /testbed
