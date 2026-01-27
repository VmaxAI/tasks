# Bug Report

### Describe the bug

I'm encountering an issue with `<script setup>` where variables defined inside nested function scopes are being incorrectly processed by the compiler. It seems like the compiler is not properly skipping function bodies when analyzing the script, which leads to unexpected behavior with variable scoping.

### Reproduction

```vue
<script setup>
const outer = ref(0)

function parentFunction() {
  const inner = ref(1)
  
  function nestedFunction() {
    const deeplyNested = ref(2)
    console.log(deeplyNested.value)
  }
  
  nestedFunction()
}

parentFunction()
</script>
```

When using nested functions like this, the compiler seems to be traversing into function bodies when it shouldn't, causing scoping issues with refs and other reactive declarations inside those functions.

### Expected behavior

The compiler should properly skip function bodies during its AST walk to avoid incorrectly analyzing variables that are scoped within those functions. Variables defined inside function scopes should be handled separately from the top-level script setup scope.

### System Info
- Vue version: 3.x
- Using SFC compiler

This appears to be related to how the compiler walks the AST and determines when to skip certain nodes during compilation.

---
Repository: /testbed
