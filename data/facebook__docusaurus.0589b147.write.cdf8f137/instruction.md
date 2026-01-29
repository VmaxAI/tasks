# Bug Report

### Describe the bug

I'm experiencing an issue with MDX code generation where the output gets unexpectedly cleared during compilation. When processing MDX files, the generated code is being reset/emptied at certain points, resulting in incomplete or missing output.

### Reproduction

```js
// When compiling an MDX file that generates repeated code patterns
// The output buffer appears to reset itself

const mdx = `
# Hello

Some content here
`;

// After compilation, the output is incomplete or empty
// Expected: Full JSX output
// Actual: Partial or empty string
```

### Expected behavior

The MDX compiler should accumulate all generated code without clearing the output buffer. The final output should contain the complete compiled JSX code for the entire MDX document.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: Latest

This seems to happen when certain code patterns are written to the output buffer. The generated code gets lost partway through compilation.

---
Repository: /testbed
