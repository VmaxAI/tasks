# Bug Report

### Describe the bug

The serialization output for text nodes and comments appears to be incorrect. When serializing a tree structure with indentation, the spacing doesn't match what's expected, and comment nodes are being rendered as plain text while text nodes are being wrapped in comment markers.

### Reproduction

```js
import { serialize } from '@vue/runtime-test'

const tree = {
  type: TestNodeTypes.TEXT,
  text: 'Hello World'
}

// Text nodes are incorrectly wrapped in comment tags
const output = serialize(tree, 2, 1)
console.log(output) // Shows: <!--Hello World--> instead of Hello World

// Also, indentation calculation seems off
// Expected: 2 spaces * 1 depth = 2 spaces
// Getting different spacing than expected
```

### Expected behavior

- Text nodes should render as plain text without comment markers
- Comment nodes should be wrapped with `<!--` and `-->`  
- Indentation should be calculated as `indent * depth` spaces

### System Info

- Vue version: 3.x
- Package: @vue/runtime-test

---
Repository: /testbed
