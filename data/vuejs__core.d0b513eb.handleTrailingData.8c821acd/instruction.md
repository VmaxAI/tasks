# Bug Report

### Describe the bug

Comments and CDATA sections are not being parsed correctly in templates. When the template contains comments or CDATA blocks, they're being treated as regular text content instead of being properly identified and handled as comments/CDATA.

### Reproduction

```vue
<template>
  <!-- This is a comment -->
  <div>Hello</div>
  <![CDATA[Some CDATA content]]>
</template>
```

When parsing this template, the comment and CDATA sections are incorrectly processed. The parser seems to be confusing the state checks and treating these special sections as text nodes.

### Expected behavior

Comments should be parsed as comments and CDATA sections should be parsed as CDATA. The parser should correctly identify when it's inside a comment-like structure (comments or CDATA) and invoke the appropriate callbacks (`oncomment` or `oncdata`) rather than treating them as text content.

### System Info

- Vue version: 3.x
- Compiler: @vue/compiler-core

This appears to be a regression in the tokenizer logic for handling trailing data in special sections.

---
Repository: /testbed
