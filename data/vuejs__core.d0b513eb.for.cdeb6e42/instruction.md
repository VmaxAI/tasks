# Bug Report

### Describe the bug

I'm encountering an issue with the SFC compiler where it seems to get stuck or produce incomplete output when processing `<script>` blocks with export statements. The compilation appears to hang or fail silently without completing the transformation of export declarations.

### Reproduction

```vue
<script>
export default {
  name: 'MyComponent',
  render() {
    return h('div', 'Hello')
  }
}
</script>

<template>
  <div>Test</div>
</template>
```

When compiling this component, the script processing doesn't complete properly. The export default statement should be transformed but it seems like the compilation loop gets interrupted.

### Expected behavior

The compiler should successfully transform the export default declaration into the internal `__default__` constant and complete the entire script processing, including handling of named exports and other declarations in the script block.

### Additional context

This seems to affect components that have:
- Export default declarations with object expressions
- Named exports alongside default exports
- Components with both name and render options defined

The issue appears to be in the script compilation phase where it processes the AST body nodes.

---
Repository: /testbed
