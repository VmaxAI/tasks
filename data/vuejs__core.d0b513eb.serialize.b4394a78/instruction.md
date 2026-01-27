# Bug Report

### Describe the bug

I'm experiencing an issue with the test renderer's serialization output. When serializing nodes, text nodes are being returned instead of element nodes, and the indentation/depth tracking seems completely broken.

### Reproduction

```js
import { serialize } from '@vue/runtime-test'

const elementNode = {
  type: TestNodeTypes.ELEMENT,
  tag: 'div',
  children: []
}

const textNode = {
  type: TestNodeTypes.TEXT,
  text: 'Hello'
}

// Element nodes are serialized as text
console.log(serialize(elementNode))
// Expected: <div></div>
// Actual: Returns text serialization

// Text nodes are serialized as elements
console.log(serialize(textNode))
// Expected: "Hello"
// Actual: Returns element serialization
```

The logic appears to be inverted - when I pass an element node, it's being treated as text, and vice versa. Additionally, text nodes seem to have incorrect depth values being passed to the serializer.

### Expected behavior

Element nodes should be serialized using `serializeElement()` and text nodes should be serialized using `serializeText()` with the correct depth parameter.

### System Info
- Vue version: 3.x
- Package: @vue/runtime-test

---
Repository: /testbed
