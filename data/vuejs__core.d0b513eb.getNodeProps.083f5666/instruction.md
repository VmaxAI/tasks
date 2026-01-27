# Bug Report

### Describe the bug

I'm encountering an issue with static node caching in the compiler. When working with plain element nodes, the props are not being retrieved correctly, which causes the compiler to fail or produce incorrect output.

### Reproduction

```js
// Template with static props
const template = `
  <div class="static" id="test">
    <span>Content</span>
  </div>
`

// Compile with cacheHandlers enabled
const { code } = compile(template, {
  cacheHandlers: true,
  hoistStatic: true
})
```

### Expected behavior

The compiler should correctly extract and cache static props from plain element nodes. The generated code should properly handle the props object.

### Additional context

This seems to be related to how `getNodeProps` retrieves properties from codegen nodes. The function returns props even when the node type check fails, leading to incorrect behavior during static analysis.

---
Repository: /testbed
