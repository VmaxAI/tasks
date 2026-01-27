# Bug Report

### Describe the bug

I'm encountering an issue with HTML comment parsing in templates. Comments are being included in the parsed output even when I explicitly disable them via the `comments` option. It seems like the behavior is inverted - comments appear when `comments: false` is set, and disappear when `comments: true` is set.

### Reproduction

```js
import { parse } from '@vue/compiler-core'

// With comments disabled
const ast1 = parse('<!-- test comment --><div>content</div>', {
  comments: false
})
// Expected: no comment nodes
// Actual: comment node is present in the AST

// With comments enabled
const ast2 = parse('<!-- test comment --><div>content</div>', {
  comments: true
})
// Expected: comment node is present
// Actual: no comment nodes in the AST
```

### Expected behavior

When `comments: false` is set in parser options, HTML comments should be stripped from the AST. When `comments: true`, they should be preserved. Currently the behavior appears to be backwards.

### System Info
- Vue version: 3.x
- Node version: 18.x

This is causing issues in production where we want to strip comments but they're being included in the compiled output instead.

---
Repository: /testbed
