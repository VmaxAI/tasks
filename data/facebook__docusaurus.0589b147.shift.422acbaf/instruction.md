# Bug Report

### Describe the bug

I'm experiencing an issue with line tracking in markdown parsing. When parsing markdown content with multiple lines, the line numbers reported in the AST nodes are incorrect. It seems like the line position tracking is off by some amount, causing all subsequent line numbers to be wrong.

### Reproduction

```js
const markdown = `# Heading

Some paragraph text.

Another paragraph.`;

const ast = remark.parse(markdown);

// The line numbers in the AST nodes don't match the actual line numbers
// For example, a node that should be on line 5 might be reported as line 3 or 4
console.log(ast.children.map(node => node.position.start.line));
```

### Expected behavior

The line numbers in the position information should accurately reflect the actual line numbers in the source markdown document. If a heading is on line 1, it should report line 1, not some other value.

### Additional context

This seems to affect any markdown document with multiple lines. The error accumulates as the parser processes more lines, so nodes further down in the document have increasingly incorrect line numbers.

---
Repository: /testbed
