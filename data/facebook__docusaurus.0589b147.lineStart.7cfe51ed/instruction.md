# Bug Report

### Describe the bug

I'm experiencing an issue where MDX content parsing seems to get stuck in an infinite loop or causes unexpected behavior when processing text chunks. The application becomes unresponsive when trying to parse certain MDX documents with paragraph content.

### Reproduction

```js
import { compile } from '@mdx-js/mdx'

const mdxContent = `
This is a simple paragraph.

Another paragraph here.
`

// This causes the parser to hang or behave unexpectedly
const result = await compile(mdxContent)
```

### Expected behavior

The MDX content should be parsed correctly and return the compiled output without hanging or causing issues. Paragraphs should be processed normally.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
