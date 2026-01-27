# Bug Report

### Describe the bug
The TypeScript compiler is throwing an error when trying to use the `generate` function from `compiler-core`. It seems like there's a type mismatch with the options parameter.

### Reproduction
```ts
import { generate } from '@vue/compiler-core'

const ast = // ... some AST node

// This throws a TypeScript error
generate(ast, {
  onContextCreated: (context) => {
    console.log(context)
  }
})
```

The error message indicates that the second parameter type is incorrect. When I try to pass an options object with `onContextCreated`, TypeScript complains about the type not matching.

### Expected behavior
The `generate` function should accept an options object with an optional `onContextCreated` callback without any TypeScript errors.

### System Info
- Vue version: 3.x
- TypeScript version: 5.x

---
Repository: /testbed
