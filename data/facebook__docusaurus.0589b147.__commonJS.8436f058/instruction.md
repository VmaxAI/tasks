# Bug Report

### Describe the bug

After a recent update, I'm encountering issues with module exports when using the MDX bundler. It appears that the CommonJS module wrapper is not properly returning the exports object, which causes imported modules to be undefined or have missing properties.

### Reproduction

```js
// When importing an MDX module
import MyComponent from './example.mdx'

// MyComponent is undefined or missing expected exports
console.log(MyComponent) // undefined or incomplete object
```

The issue seems to affect any CommonJS-style modules that are processed through the MDX loader. The exports object isn't being returned correctly from the require wrapper function.

### Expected behavior

Imported MDX modules should expose their exports correctly, with all exported components and values being accessible.

### System Info
- MDX version: 3.0.0
- Build tool: Jest/bundler with MDX support

---
Repository: /testbed
