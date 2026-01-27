# Bug Report

### Describe the bug

When parsing template attributes, the compiler is not properly handling the end of attribute names. After updating, I noticed that attribute parsing seems to be broken in certain cases - the parser doesn't correctly transition states when it encounters the equals sign after an attribute name.

### Reproduction

```vue
<template>
  <div class="test" id="myDiv"></div>
</template>
```

When the compiler processes attributes like `class="test"`, it should properly recognize the `=` character as the end of the attribute name and transition to parsing the attribute value. However, it appears that the state transition logic has been disrupted.

### Expected behavior

The compiler should correctly parse attribute names and properly handle the transition to attribute value parsing when encountering the `=` character. The attribute name should be captured and the parser should move to the next state to handle the attribute value.

### System Info
- Vue version: 3.x
- Environment: Both browser and SSR

---
Repository: /testbed
