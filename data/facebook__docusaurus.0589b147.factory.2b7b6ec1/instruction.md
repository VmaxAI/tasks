# Bug Report

### Describe the bug

After a recent update, MDX processing appears to be broken. When trying to compile MDX files, the process seems to hang or fail silently without producing any output. This is affecting our entire documentation build pipeline.

### Reproduction

```js
import { compile } from '@mdx-js/mdx'

const mdxContent = `
# Hello World

This is a test MDX file with some content.

<CustomComponent />
`

// This hangs or fails to complete
const result = await compile(mdxContent)
```

### Expected behavior

The MDX content should compile successfully and return the compiled output. The compilation should complete without hanging.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

This started happening after updating the vendor files. Rolling back to the previous version resolves the issue, so it seems to be related to recent changes in the tree traversal logic.

---
Repository: /testbed
