# Bug Report

### Describe the bug

After a recent update, the generated code from the compiler is producing incorrect helper function names. Instead of using the proper helper names like `_createVNode`, `_toDisplayString`, etc., the output is generating invalid references with `$` prefix followed by numeric keys.

### Reproduction

```js
import { compile } from '@vue/compiler-core'

const template = `<div>{{ message }}</div>`
const result = compile(template)

console.log(result.code)
// Expected: Functions like _createVNode, _toDisplayString
// Actual: Functions like $1, $2, etc.
```

The compiled output contains references like `$1`, `$2` instead of the expected `_createVNode`, `_toDisplayString` helper names. This causes runtime errors when the generated code is executed since these helper references don't exist.

### Expected behavior

The compiler should generate proper helper function names (e.g., `_createVNode`, `_toDisplayString`) that correspond to actual runtime helpers, not numeric keys.

### System Info
- Vue version: 3.x
- Compiler package: @vue/compiler-core

---
Repository: /testbed
