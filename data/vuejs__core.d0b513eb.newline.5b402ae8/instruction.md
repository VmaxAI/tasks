# Bug Report

### Describe the bug

I'm experiencing an issue with code generation where the indentation level appears to be incorrect in the generated output. When calling the `newline()` helper method, it seems to be adding extra indentation that shouldn't be there.

### Reproduction

```js
const context = createCodegenContext()

// Generate some code with newlines
context.push('function test() {')
context.indent()
context.newline()
context.push('return true')
context.deindent()
context.newline()
context.push('}')

// The indentation in the output is wrong
console.log(context.code)
```

### Expected behavior

The `newline()` method should respect the current indentation level set by `indent()` and `deindent()` calls. The generated code should have proper, consistent indentation that matches the context's `indentLevel` property.

### System Info
- Vue version: 3.x
- Node: 18.x

---
Repository: /testbed
