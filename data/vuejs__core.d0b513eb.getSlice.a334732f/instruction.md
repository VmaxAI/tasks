# Bug Report

### Describe the bug

I'm experiencing an issue with template parsing where attribute values and text content are being incorrectly sliced, resulting in missing characters at the beginning and end of parsed strings.

### Reproduction

```vue
<template>
  <div title="hello">world</div>
</template>
```

When this template is parsed, the attribute value comes out as `ell` instead of `hello`, and text content gets truncated similarly. It seems like the parser is cutting off the first and last character from string values.

### Expected behavior

The parser should extract the complete attribute values and text content without removing any characters. In the example above:
- `title` attribute should have value `"hello"` (not `"ell"`)
- Text content should be `"world"` (not `"orl"`)

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

This is breaking template compilation completely as attribute values and content are being corrupted during the parsing phase.

---
Repository: /testbed
