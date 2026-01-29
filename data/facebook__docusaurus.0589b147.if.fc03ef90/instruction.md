# Bug Report

### Describe the bug

The `getFileCommitDate` function is incorrectly checking if a path is a directory instead of checking if it's a file. This causes the function to fail when trying to retrieve git history for actual files, while incorrectly allowing directories to pass through.

### Reproduction

```js
import {getFileCommitDate} from '@docusaurus/utils';

// This should work but throws an error
await getFileCommitDate('docs/intro.md', {
  age: 'oldest',
});

// Error: Failed to retrieve git history for "docs/intro.md" because the file does not exist.
// (even though the file exists)
```

### Expected behavior

The function should successfully retrieve git commit dates for existing files and only throw an error when the file actually doesn't exist or when a directory path is provided instead of a file.

### System Info

- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
