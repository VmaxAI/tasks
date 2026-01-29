# Bug Report

### Describe the bug

I'm experiencing an issue with document container continuation in MDX parsing. When processing nested containers, the stack state appears to be getting corrupted or improperly managed, leading to unexpected parsing behavior.

### Reproduction

```js
// Create a document with nested containers
const mdxContent = `
> Outer container
> > Nested container
> > Content here
`;

// Parse the MDX content
const result = compile(mdxContent);
```

When parsing documents with nested block containers (like nested blockquotes), the parser seems to lose track of the container state. The stack that manages container nesting doesn't maintain the proper state information, which causes issues with continuation logic.

### Expected behavior

Nested containers should be properly tracked with their full state preserved on the stack. Each level of nesting should maintain both the construct information and its associated container state so that continuation can be properly handled.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
