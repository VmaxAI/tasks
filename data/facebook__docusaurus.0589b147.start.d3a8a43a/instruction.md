# Bug Report

### Describe the bug

I'm experiencing an issue with directive text parsing where the order of operations seems to be causing problems. When parsing text directives (like `:directive[text]`), the parser appears to be entering/exiting tokens in the wrong sequence, which is affecting the resulting AST structure.

### Reproduction

```js
// Parse a simple text directive
const ast = parse(':myDirective[some text]')

// The resulting AST has incorrect token ordering
// directiveText and directiveTextMarker are in wrong order
```

When I inspect the parsed output, the token hierarchy doesn't match what I'd expect - it looks like `directiveText` and `directiveTextMarker` are being entered in an unexpected order.

### Expected behavior

The parser should enter `directiveText` first, then `directiveTextMarker`, and the callbacks should be passed in the correct order (`ok` before `nok`). The AST structure should properly reflect the nesting of directive elements.

### Additional context

This might be related to how the `factoryName` callback is being invoked - the argument order seems off compared to other similar tokenizer functions in the codebase.

---
Repository: /testbed
