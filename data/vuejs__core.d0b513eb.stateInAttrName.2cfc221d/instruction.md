# Bug Report

### Describe the bug

When parsing template attributes, the tokenizer is not correctly handling attribute names that contain equals signs. The condition check appears to be inverted, causing attributes with `=` in their names to be parsed incorrectly.

### Reproduction

```vue
<template>
  <div data-value="test"></div>
  <input type="text" name="field">
</template>
```

When compiling templates with standard HTML attributes that use the equals sign (like `data-value="test"`), the attribute name parsing doesn't work as expected. The tokenizer seems to skip over the equals sign check entirely.

### Expected behavior

Attributes should be parsed correctly when they contain an equals sign followed by a value. The attribute name should be captured up to the `=` character, and then the value parsing should begin.

### Additional context

This affects basic attribute parsing in templates. Even simple attributes with values are not being tokenized properly, which breaks template compilation for common HTML patterns.

---
Repository: /testbed
