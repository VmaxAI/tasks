# Bug Report

### Describe the bug
When parsing template tags, the tokenizer is not correctly handling tag names. It appears that tag name processing is being skipped in certain cases, which causes parsing errors or incorrect AST generation for valid HTML/template syntax.

### Reproduction
```vue
<template>
  <div>
    <custom-component />
    <another-tag></another-tag>
  </div>
</template>
```

When the compiler tries to parse templates with various tag structures, the tag names are not being processed correctly. This affects both self-closing tags and regular opening/closing tag pairs.

### Expected behavior
The tokenizer should properly recognize and process tag names during the parsing phase, allowing the compiler to generate the correct AST for all valid template syntax.

### System Info
- Vue version: 3.x
- Build tool: Vite

---
Repository: /testbed
