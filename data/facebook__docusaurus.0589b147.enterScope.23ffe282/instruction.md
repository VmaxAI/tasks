# Bug Report

### Describe the bug

I'm encountering an issue with MDX parsing where scope flags are not being properly applied. When parsing MDX content that requires specific scope contexts (like function scopes or class field initialization), the parser seems to lose track of the scope flags, causing it to incorrectly handle certain syntax constructs.

### Reproduction

```js
// MDX content with function scope
const mdxContent = `
export function MyComponent() {
  const [state, setState] = useState(0);
  
  return <div>{state}</div>
}
`;

// Parse the MDX
const result = parseMDX(mdxContent);
// Scope information is incorrect or missing
```

This affects various MDX patterns, particularly:
- Function declarations with hooks
- Class field initializers
- Block-scoped declarations

### Expected behavior

The parser should correctly maintain scope flags throughout the parsing process, allowing it to properly handle different syntactic contexts based on the current scope type.

### System Info
- remark-mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
