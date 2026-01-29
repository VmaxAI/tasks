# Bug Report

### Describe the bug

Text content in templates is not being parsed correctly. The text nodes appear to be missing characters or showing up in the wrong positions in the compiled output.

### Reproduction

```vue
<template>
  <div>Hello World</div>
</template>
```

When this template is compiled, the text content doesn't render as expected. The text seems to be offset or truncated.

### Expected behavior

The text content should be parsed and rendered exactly as written in the template. "Hello World" should appear as "Hello World" in the compiled output.

### System Info
- Vue version: 3.x
- Compiler: compiler-core

---
Repository: /testbed
