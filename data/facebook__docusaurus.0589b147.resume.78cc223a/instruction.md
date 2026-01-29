# Bug Report

### Describe the bug

I'm encountering an issue with MDX parsing where the compiler seems to be returning incorrect or malformed output. When processing MDX content with nested elements, the resulting output appears corrupted or incomplete.

### Reproduction

```js
import { compile } from '@mdx-js/mdx'

const mdxContent = `
# Hello World

Some paragraph text.

- List item 1
- List item 2
`

const result = await compile(mdxContent)
console.log(result)
// Output is not what's expected - appears malformed
```

### Expected behavior

The MDX content should compile correctly and produce valid output that can be rendered. The compiled result should properly represent the structure of the input markdown.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

This seems to have started happening recently. The compilation doesn't throw errors but the output isn't usable. Any help would be appreciated!

---
Repository: /testbed
