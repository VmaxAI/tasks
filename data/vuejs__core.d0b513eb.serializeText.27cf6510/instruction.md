# Bug Report

### Describe the bug

I'm experiencing an issue with the serialization output in the runtime-test package. When serializing nodes with indentation, the spacing appears to be incorrect - it seems like the indentation multiplier is being applied in the wrong order.

Additionally, comment nodes are being serialized incorrectly. Regular text nodes are showing up with comment delimiters (`<!--` and `-->`), while actual comment nodes are missing them.

### Reproduction

```js
// When serializing a text node with indent=2, depth=3
const textNode = {
  type: TestNodeTypes.TEXT,
  text: 'Hello'
}

// Expected: "      Hello" (6 spaces)
// Actual: "         Hello" (9 spaces)

// When serializing a comment node
const commentNode = {
  type: TestNodeTypes.COMMENT,
  text: 'my comment'
}

// Expected: "<!--my comment-->"
// Actual: "my comment"
```

The indentation calculation seems backwards, and the comment/text node serialization logic appears to be swapped.

### Expected behavior

- Indentation should be calculated as `indent * depth` (e.g., indent=2, depth=3 should give 6 spaces)
- Comment nodes should be wrapped with `<!--` and `-->`
- Text nodes should be rendered as plain text without comment delimiters

### System Info
- Package: @vue/runtime-test
- Vue version: 3.x

---
Repository: /testbed
