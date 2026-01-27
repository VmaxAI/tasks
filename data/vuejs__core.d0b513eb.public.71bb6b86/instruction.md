# Bug Report

### Describe the bug

I'm experiencing an issue with template parsing where templates appear to have an extra space character at the beginning. This is causing unexpected behavior in my components where the rendered output starts with whitespace that shouldn't be there.

### Reproduction

```vue
<template>
  <div>Hello World</div>
</template>
```

When this template is compiled and rendered, there's an unexpected space character before the content. It seems like the parser is initializing with a space in the buffer instead of starting empty.

### Expected behavior

The template should be parsed without any leading whitespace being added. The output should match exactly what's in the template source without any extra characters being inserted at the beginning.

### Additional context

This appears to affect all templates regardless of their content. The issue manifests as:
- Extra whitespace in rendered output
- Incorrect character positioning in the parsed AST
- Potential offset issues when trying to map back to source locations

Not sure when this started happening but it's causing issues with text content and layout in my application.

---
Repository: /testbed
