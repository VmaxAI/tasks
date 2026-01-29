# Bug Report

### Describe the bug

After a recent update, I'm getting a syntax error when trying to use the MDX compiler. The build fails immediately with an error about an unexpected token.

### Reproduction

```js
import { compile } from '@mdx-js/mdx'

const mdxSource = `
# Hello World

This is a test MDX file.
`

// This throws a syntax error
const result = await compile(mdxSource)
```

### Expected behavior

The MDX source should compile successfully without any syntax errors. This was working fine in previous versions.

### Error message

```
SyntaxError: Unexpected token 'function'
```

The error seems to be coming from somewhere in the vendor bundle, but I can't pinpoint exactly where. It happens as soon as I try to import or use anything from `@mdx-js/mdx`.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
