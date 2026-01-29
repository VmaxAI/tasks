# Bug Report

### Describe the bug

I'm encountering an issue where MDX content is not rendering properly. When I try to compile MDX files, the output is empty or undefined instead of showing the expected JSX/React components.

### Reproduction

```js
import { compile } from '@mdx-js/mdx'

const mdxContent = `
# Hello World

This is a test paragraph.
`

const result = await compile(mdxContent)
// result is undefined or empty instead of compiled JSX
```

### Expected behavior

The MDX content should be compiled into valid JSX output that can be rendered. The compiled result should contain the heading and paragraph elements.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

This seems to have started recently. Previously the same code was working fine and returning the compiled output as expected.

---
Repository: /testbed
