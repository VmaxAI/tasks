# Bug Report

### Describe the bug

I'm encountering an issue with HTML nesting validation in the compiler. It seems like valid parent-child element combinations are being incorrectly flagged as invalid, and invalid combinations are being allowed through.

### Reproduction

When compiling templates with nested HTML elements, the validation logic appears to be inverted. For example:

```vue
<template>
  <table>
    <tr>
      <td>Content</td>
    </tr>
  </table>
</template>
```

This valid HTML structure is being rejected by the compiler, while invalid nesting patterns are not being caught.

Similarly, elements that should only accept specific children (like `<select>` should only contain `<option>` elements) are now accepting any child elements, and valid children are being rejected.

### Expected behavior

The HTML nesting validation should:
- Allow valid parent-child combinations (e.g., `<table>` containing `<tr>`)
- Reject invalid parent-child combinations
- Properly validate elements with restricted child elements
- Properly validate elements with restricted parent elements

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-dom

This seems to have started recently and is causing compilation errors for previously working templates.

---
Repository: /testbed
