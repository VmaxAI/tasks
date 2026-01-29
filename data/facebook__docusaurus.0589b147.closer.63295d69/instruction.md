# Bug Report

### Describe the bug

I'm experiencing an issue with MDX compilation where the compiler seems to be executing callback functions prematurely or incorrectly. The behavior appears to be related to how closers/exit handlers are being called during the parsing process.

### Reproduction

When compiling MDX content with nested structures (like JSX components with children), the compilation either fails silently or produces incorrect output. It seems like the exit callbacks are being invoked at the wrong time or with incorrect parameters.

```js
const mdx = `
# Hello

<Component>
  <NestedComponent>
    Content here
  </NestedComponent>
</Component>
`

// Compilation produces unexpected results
const result = compile(mdx)
```

### Expected behavior

The MDX compiler should properly handle nested component structures and call exit handlers at the appropriate times when closing tags/nodes. The compiled output should correctly represent the nested structure.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

This seems like it might be related to how the token stack is being managed during the compilation process. The issue appears to affect any MDX content with nested elements.

---
Repository: /testbed
