# Bug Report

### Describe the bug

After a recent update, the MDX parser appears to be broken. When trying to parse any MDX content, the tokenizer seems to be incomplete or corrupted, causing parsing to fail entirely.

### Reproduction

```js
import { compile } from '@mdx-js/mdx'

const mdxContent = `
# Hello World

This is a simple MDX document.
`

// This fails to parse
const result = await compile(mdxContent)
```

### Expected behavior

The MDX content should be parsed successfully and converted to JSX without errors. The tokenizer should handle the markdown constructs properly.

### Additional context

This seems to have started happening after the latest changes. The parser worked fine before but now any attempt to compile MDX content results in failures. It looks like something might have gotten truncated or corrupted in the tokenizer logic, specifically in the `constructFactory` function.

---
Repository: /testbed
