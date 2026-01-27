# Bug Report

### Describe the bug

When using `pipeToNodeWritable()` for server-side rendering, empty string content is being written to the stream before ending it. This causes unexpected output in the rendered HTML, particularly when components render empty strings as part of their normal output.

### Reproduction

```js
import { createSSRApp } from 'vue'
import { pipeToNodeWritable } from 'vue/server-renderer'
import { Writable } from 'stream'

const app = createSSRApp({
  template: '<div>{{ content }}</div>',
  data() {
    return { content: '' }
  }
})

const writable = new Writable({
  write(chunk, encoding, callback) {
    console.log('Chunk:', chunk.toString())
    callback()
  }
})

pipeToNodeWritable(app, {}, writable)
```

### Expected behavior

Empty strings should be treated the same as `null` values - they shouldn't trigger an additional write to the stream before ending. The stream should just end cleanly without writing empty content.

### System Info
- Vue version: 3.x
- Node.js version: 18.x
- Server renderer: latest

---
Repository: /testbed
