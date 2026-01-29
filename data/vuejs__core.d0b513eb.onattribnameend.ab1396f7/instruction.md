# Bug Report

### Describe the bug

I'm experiencing an issue where duplicate attribute detection in templates isn't working correctly. When I define the same attribute multiple times on an element, the compiler doesn't throw an error as expected. Even more concerning, it seems like the attribute name parsing might be off by one character.

### Reproduction

```vue
<template>
  <div id="test" id="test">
    <!-- This should error but doesn't -->
  </div>
  
  <button class="btn" class="btn-primary">
    <!-- Duplicate class attributes not detected -->
  </button>
</template>
```

Also noticed that when I use attributes with certain names, they seem to be parsed incorrectly - like the first character is being skipped or something.

### Expected behavior

The compiler should detect duplicate attributes and emit a `DUPLICATE_ATTRIBUTE` error. Currently it's not catching these cases at all.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

---
Repository: /testbed
