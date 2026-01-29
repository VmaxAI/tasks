# Bug Report

### Describe the bug

Source maps are not being generated when using the MDX compiler. After compiling MDX content, the returned `map` property is always `undefined` even when a `SourceMapGenerator` is provided in the options.

### Reproduction

```js
import { compile } from '@mdx-js/mdx'
import { SourceMapGenerator } from 'source-map'

const mdxContent = `
# Hello World

This is some MDX content.
`

const result = await compile(mdxContent, {
  SourceMapGenerator,
  filePath: 'test.mdx'
})

console.log(result.map) // Expected: source map object, Actual: undefined
```

### Expected behavior

When `SourceMapGenerator` is provided in the compilation options, the result should include a valid source map object in the `map` property. This is needed for debugging and proper error reporting in development tools.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
