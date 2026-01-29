# Bug Report

### Describe the bug

When importing MDX components using default import syntax, the component names are not being recognized correctly in the table of contents. This appears to affect how default imports are resolved in MDX files.

### Reproduction

```js
// In an MDX file
import MyComponent from './MyComponent';

# Using the component
<MyComponent />
```

The default import name lookup seems to be failing, causing components imported this way to not be properly processed.

### Expected behavior

Default imports should be correctly identified and their names should be extractable for use in TOC generation and component resolution.

### System Info
- Docusaurus version: latest
- Package: @docusaurus/mdx-loader

---
Repository: /testbed
