# Bug Report

### Describe the bug

When processing MDX files, the file format detection logic appears to be inverted. Files with `.md` extensions are being treated as MDX format, and files with `.mdx` extensions are being treated as MD format. This causes incorrect parsing and processing of markdown/MDX content.

### Reproduction

```js
// Create a file with .md extension
const mdFile = 'example.md';
// The file is incorrectly detected as 'mdx' format

// Create a file with .mdx extension  
const mdxFile = 'example.mdx';
// The file is incorrectly detected as 'md' format
```

### Expected behavior

- Files with `.md` extension should be detected as `'md'` format
- Files with `.mdx` extension should be detected as `'mdx'` format
- The format detection should correctly identify the file type based on the extension

### System Info

- Docusaurus version: latest
- Node version: 18.x

This is causing issues with our documentation site where MDX components in `.mdx` files aren't being processed correctly, and standard markdown files are being parsed as MDX when they shouldn't be.

---
Repository: /testbed
