# Bug Report

### Describe the bug

After a recent update, I'm seeing issues with how root nodes are being transformed in the MDX processing pipeline. The order of operations for wrapping and patching seems to have changed, which is causing unexpected behavior in the output structure.

### Reproduction

When processing MDX content with root-level elements, the transformation doesn't produce the expected structure. Here's a minimal example:

```js
import { compile } from '@mdx-js/mdx'

const mdxContent = `
# Hello World

Some content here.
`

const result = await compile(mdxContent)
// The resulting AST structure is not wrapped correctly
```

### Expected behavior

The root node should be:
1. Transformed with `state.all(node)`
2. Have data applied via `state.applyData()`
3. Be patched with `state.patch()`
4. Finally wrapped with `state.wrap()`

Instead, it appears the wrapping is happening at the wrong stage, before the data transformation is applied.

### System Info

- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

This is affecting our documentation site where we rely on the correct AST structure for custom transformations. Any help would be appreciated!

---
Repository: /testbed
