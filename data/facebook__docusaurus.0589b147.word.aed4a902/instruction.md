# Bug Report

### Describe the bug

I'm experiencing an issue with MDX import statements not being recognized correctly. When I try to use `import` statements in my MDX files, they're not being parsed properly and the content isn't rendering as expected.

### Reproduction

```mdx
import { Component } from './component'

# My Document

<Component />
```

The import statement seems to be ignored or treated as regular content instead of being processed as an ESM import. This causes the component to not be available in the document scope.

### Expected behavior

Import statements at the beginning of MDX files should be properly parsed and the imported modules should be available for use in the document. The parser should recognize `import` followed by a space as the start of an ESM import statement.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
