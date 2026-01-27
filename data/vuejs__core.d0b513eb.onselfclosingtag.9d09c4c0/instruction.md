# Bug Report

### Describe the bug

I'm experiencing an issue with self-closing tags in templates. When using self-closing tags like `<component />`, the parser seems to be handling the tag stack incorrectly, which causes problems with nested components or elements.

### Reproduction

```vue
<template>
  <div>
    <MyComponent />
    <p>Some text</p>
  </div>
</template>
```

When parsing templates with self-closing tags, the component hierarchy gets messed up. It seems like the parser is not correctly managing which element should be closed when encountering a self-closing tag.

### Expected behavior

Self-closing tags should be properly parsed and closed without affecting the parent element stack. The template should compile correctly and maintain the proper nesting structure.

### System Info
- Vue version: 3.x
- Build tool: Vite

---
Repository: /testbed
