# Bug Report

### Describe the bug

I'm experiencing a crash when parsing MDX content. The parser throws an error about being unable to read properties of undefined when trying to process certain MDX files.

### Reproduction

```js
const parser = require('remark-mdx');

// Trying to parse any MDX content results in an error
const content = `
# Hello

Some content here
`;

parser.parse(content);
// TypeError: Cannot read properties of undefined (reading 'length')
```

### Expected behavior

The parser should successfully parse the MDX content without throwing errors. This was working fine in previous versions.

### System Info
- remark-mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
