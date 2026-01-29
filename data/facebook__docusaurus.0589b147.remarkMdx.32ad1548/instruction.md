# Bug Report

### Describe the bug

I'm experiencing an issue with MDX parsing after a recent update. It seems like the parser is not correctly processing MDX content anymore. When I try to parse MDX files, I'm getting unexpected errors or the content is not being transformed properly.

### Reproduction

```js
import { compile } from '@mdx-js/mdx'

const mdxContent = `
# Hello World

<CustomComponent prop="value" />

Some text here.
`

const result = await compile(mdxContent)
// Parser fails or produces incorrect output
```

### Expected behavior

The MDX content should be parsed and compiled correctly, with JSX components and markdown content properly transformed. The micromark extensions and markdown transformers should be applied in the correct order.

### System Info

- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

This seems to have started happening recently. The parsing worked fine before but now it's breaking on what should be valid MDX syntax.

---
Repository: /testbed
