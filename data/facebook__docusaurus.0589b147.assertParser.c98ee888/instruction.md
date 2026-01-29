# Bug Report

### Describe the bug

I'm encountering an issue where the MDX processor throws a `TypeError` when trying to parse content, even though a valid parser is configured. The error message says "Cannot `[method]` without `parser`" but the parser is definitely set.

### Reproduction

```js
import {unified} from '@mdx-js/mdx'
import remarkParse from 'remark-parse'

const processor = unified()
  .use(remarkParse)
  .use(/* other plugins */)

// This throws: TypeError: Cannot `parse` without `parser`
const result = processor.parse('# Hello World')
```

### Expected behavior

The processor should successfully parse the MDX content when a parser plugin is properly configured. The error should only be thrown when no parser is actually provided.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
