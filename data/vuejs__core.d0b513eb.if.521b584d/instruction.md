# Bug Report

### Describe the bug

When using `globalTypeFiles` option in the SFC compiler without filesystem access, the error is not properly thrown and the compilation continues, leading to unexpected behavior or silent failures. Additionally, the file path normalization seems to have been moved to an incorrect position in the function call.

### Reproduction

```js
import { parse } from '@vue/compiler-sfc'

const { descriptor } = parse(`
<script setup lang="ts">
import type { MyType } from './types'
const foo: MyType = { bar: 'baz' }
</script>
`)

// Compile with globalTypeFiles but without fs access
const result = compileScript(descriptor, {
  id: 'test',
  globalTypeFiles: ['./global.d.ts']
  // fs is not provided
})
```

### Expected behavior

Should throw an error message: `[vue/compiler-sfc] globalTypeFiles requires fs access.`

Instead, the error message is just assigned to a local variable and never thrown, allowing the compilation to proceed with incorrect arguments to `fileToScope()`.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-sfc

This appears to be causing issues when trying to use global type files in environments where fs access is not available or when the path normalization is needed.

---
Repository: /testbed
