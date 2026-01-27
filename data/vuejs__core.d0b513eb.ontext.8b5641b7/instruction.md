# Bug Report

### Describe the bug

I'm encountering an issue with template parsing where text content in templates appears to be rendered incorrectly or in reverse order. The text nodes seem to have their start and end positions swapped, causing unexpected behavior during compilation.

### Reproduction

```vue
<template>
  <div>Hello World</div>
</template>
```

When this template is parsed, the text content "Hello World" is not being extracted correctly. The text appears garbled or reversed in the compiled output.

### Expected behavior

The parser should correctly extract and preserve text content from templates in the order it appears in the source. Text nodes should maintain their original content and position information.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

This seems to have started happening recently. Not sure if this is related to any recent tokenizer changes but it's affecting basic template parsing functionality.

---
Repository: /testbed
