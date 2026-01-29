# Bug Report

### Describe the bug

After a recent update, MDX content parsing seems to be broken. When trying to parse MDX files, the content is not being processed correctly and the parser appears to skip over the actual content parsing step entirely.

### Reproduction

```js
import { compile } from '@mdx-js/mdx'

const mdxContent = `
# Hello World

This is some content.
`

const result = await compile(mdxContent)
// The content is not parsed correctly
```

### Expected behavior

The MDX content should be properly tokenized and parsed. The parser should enter the content state and process the chunk content before moving to the next step.

### Additional context

This seems to have started happening after a recent change to the content tokenization logic. The content tokenizer appears to be returning early without actually processing the content chunks.

---
Repository: /testbed
