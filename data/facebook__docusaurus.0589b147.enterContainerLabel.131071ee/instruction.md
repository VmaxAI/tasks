# Bug Report

### Describe the bug

I'm encountering an issue with container directive labels in remark-directive. When parsing container directives with labels, the label content is not being properly structured in the resulting AST. The label appears to be treated incorrectly, which causes downstream processing issues.

### Reproduction

```js
import remarkParse from 'remark-parse'
import remarkDirective from 'remark-directive'
import { unified } from 'unified'

const processor = unified()
  .use(remarkParse)
  .use(remarkDirective)

const markdown = `
:::note[This is a label]
Content here
:::
`

const ast = processor.parse(markdown)
const result = processor.runSync(ast)

console.log(JSON.stringify(result, null, 2))
```

### Expected behavior

The label should be parsed as a paragraph node within the container directive structure. The AST should properly represent the label with `type: "paragraph"` and include the children nodes for the label text.

### Actual behavior

The label is being parsed with an incorrect node type, which breaks the expected AST structure for container directives with labels.

### System Info
- remark-directive version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
