# Bug Report

### Describe the bug

I'm encountering an issue when rendering MDX links where the position information seems to be getting lost or applied incorrectly. The links are rendering, but their source position metadata isn't being preserved properly in the generated output.

### Reproduction

```jsx
import { compile } from '@mdx-js/mdx'

const mdxContent = `
[Link text](https://example.com)
`

const result = await compile(mdxContent, {
  // position tracking enabled
})

// The resulting link element doesn't have correct position data
console.log(result)
```

When I inspect the output, the position information for link nodes appears to be missing or incorrectly applied to the generated AST nodes.

### Expected behavior

Link elements should maintain their source position information from the original MDX content, allowing proper source mapping and debugging capabilities.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

This seems to have started recently - position data was working correctly in earlier versions. The links themselves render fine, but tools that depend on position metadata (like error reporting and source maps) are affected.

---
Repository: /testbed
