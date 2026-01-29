# Bug Report

### Describe the bug

I'm experiencing an issue with the template parser where self-closing tags are not being handled correctly. When parsing templates with self-closing elements like `<img />` or `<input />`, the parser seems to skip processing the tag end properly in certain scenarios.

### Reproduction

```vue
<template>
  <div>
    <img src="test.jpg" />
    <input type="text" />
  </div>
</template>
```

When this template is parsed, the self-closing tags don't get processed as expected. The issue appears to be related to how the parser handles the tag end position.

### Expected behavior

Self-closing tags should be parsed correctly and the parser should properly handle the end position of these tags. The compiled output should treat self-closing elements the same way regardless of whether they have attributes or not.

### System Info
- Vue version: 3.x
- Template compiler: latest

---
Repository: /testbed
