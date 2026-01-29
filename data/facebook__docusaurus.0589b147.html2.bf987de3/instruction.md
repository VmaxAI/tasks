# Bug Report

### Describe the bug

I'm experiencing an issue with HTML node handling in the remark parser. When parsing markdown content that contains HTML blocks, the parser is generating nodes with incorrect type and value properties.

### Reproduction

```js
import {remark} from 'remark'

const markdown = `
Some text

<div>HTML content</div>

More text
`

const result = remark().parse(markdown)

// Inspect the HTML node
console.log(result.children.find(node => node.type === 'html'))
// Expected: { type: 'html', value: '<div>HTML content</div>' }
// Actual: { type: 'htm', value: null }
```

### Expected behavior

HTML nodes should have:
- `type` property set to `"html"`
- `value` property containing the actual HTML string content

Instead, the nodes have `type: "htm"` and `value: null`, which breaks any downstream processing that relies on proper HTML node structure.

### System Info
- remark version: 15.0.1
- Node.js version: 18.x

This is breaking my markdown-to-html pipeline as the HTML passthrough content is not being preserved correctly.

---
Repository: /testbed
