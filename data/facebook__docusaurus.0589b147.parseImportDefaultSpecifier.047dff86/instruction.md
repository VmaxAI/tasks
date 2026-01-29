# Bug Report

### Describe the bug

I'm encountering an issue with import default specifiers in MDX files. When parsing import statements with default imports, the validation seems to be checking the wrong node, which causes problems with the parsed AST structure.

### Reproduction

```js
import React from 'react'
import { useState } from 'react'

export default function MyComponent() {
  return <div>Hello</div>
}
```

When parsing the above MDX content, the default import specifier (`React`) is not being validated correctly. The issue appears to be related to how the parser handles the node structure during import parsing.

### Expected behavior

Default import specifiers should be properly validated and the resulting AST node should have the correct structure with validation applied to the appropriate node properties.

### System Info
- remark-mdx version: 3.0.0
- Node version: Latest

---
Repository: /testbed
