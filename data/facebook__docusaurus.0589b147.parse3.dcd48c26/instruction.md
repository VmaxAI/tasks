# Bug Report

### Describe the bug

After a recent update, MDX parsing seems to be broken. The parser is no longer recognizing markdown constructs properly, and documents that previously parsed correctly are now failing or producing incorrect output.

### Reproduction

```js
import { compile } from '@mdx-js/mdx'

const mdxContent = `
# Hello World

This is a paragraph with **bold** text.

- List item 1
- List item 2
`

const result = await compile(mdxContent)
// Parser doesn't recognize markdown constructs correctly
```

### Expected behavior

The MDX content should be parsed correctly with all markdown constructs (headings, bold text, lists, etc.) being recognized and transformed properly. The parser should use the configured constructs from the extensions.

### Additional context

This appears to have started happening recently. Documents that used to work are now not being parsed correctly. It seems like the parser might not be using the right construct definitions.

---
Repository: /testbed
