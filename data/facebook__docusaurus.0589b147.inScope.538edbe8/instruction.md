# Bug Report

### Describe the bug

I'm experiencing an issue with scope checking in MDX where variables declared in the top-level scope are not being recognized. It seems like the scope resolution is stopping prematurely and not checking the root scope.

### Reproduction

```jsx
export const myVariable = 'test value'

# My Document

{myVariable}
```

When trying to reference a variable that's declared at the top level (exported or in the root scope), it's not being found during compilation. The variable should be accessible but the scope checker appears to be skipping the root scope level.

### Expected behavior

Variables declared in the top-level/root scope should be properly detected and accessible throughout the MDX document. The scope checking should traverse all the way up to the root scope, not just parent scopes.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
