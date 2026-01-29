# Bug Report

### Describe the bug

I'm encountering an issue where passing certain types of values is no longer working correctly. It seems like the type checking logic is rejecting valid inputs that should be accepted.

### Reproduction

```js
// This should work but doesn't
const result = processValue(new Uint8Array([1, 2, 3]))

// This also fails
const buffer = Buffer.from('test')
processValue(buffer)
```

Both of these examples should be valid inputs, but they're being rejected. It looks like the validation is too strict now and only accepts values that meet ALL conditions instead of ANY of them.

### Expected behavior

The function should accept either string values OR Uint8Array/buffer values, not require both at the same time. Previously this was working fine.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
