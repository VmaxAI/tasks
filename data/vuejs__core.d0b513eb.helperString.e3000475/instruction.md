# Bug Report

### Describe the bug

I'm experiencing an issue with helper function names in the compiled output. It seems like the underscore prefix that should be present in helper function calls is missing, which is causing runtime errors when the generated code tries to reference helpers.

### Reproduction

When compiling a template that uses runtime helpers, the generated code contains incorrect helper references without the expected underscore prefix. For example:

```js
// Expected output should be something like:
return _createVNode(...)

// But instead getting:
return createVNode(...)
```

This causes the compiled template to fail at runtime because the helper functions aren't properly namespaced.

### Expected behavior

Helper function calls in the compiled output should include the underscore prefix (e.g., `_createVNode`, `_toDisplayString`, etc.) to properly reference the runtime helpers.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

---
Repository: /testbed
