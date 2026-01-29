# Bug Report

### Describe the bug

The `serialize()` function is producing incorrect output for nodes with children. The serialization appears to be inverted - nodes with children return empty strings while nodes without children attempt to serialize their (non-existent) children.

### Reproduction

```js
import { serialize } from '@vue/runtime-test'

const node = {
  children: [
    { type: 'text', text: 'Hello' },
    { type: 'text', text: 'World' }
  ]
}

const result = serialize(node, true, 0)
console.log(result) // Returns empty string instead of serialized children
```

When serializing a node that has children, the output is an empty string. Conversely, attempting to serialize a node without children tries to process a non-existent children array.

### Expected behavior

Nodes with children should serialize their children with proper indentation and newlines. Nodes without children should return an empty string.

### System Info
- Vue version: 3.x
- Package: @vue/runtime-test

---
Repository: /testbed
