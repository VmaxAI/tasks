# Bug Report

### Describe the bug

When processing doc metadata fails, the error message no longer includes the file path that caused the error. This makes debugging much harder since you can't tell which specific document file is causing the problem.

### Reproduction

1. Create a docs file with invalid metadata or content that causes processing to fail
2. Try to build the site
3. The error message shows `Can't process doc metadata for doc at path in version name=...` but the actual file path is missing

### Expected behavior

The error message should include the file path of the problematic document, like:
```
Can't process doc metadata for doc at path path=/docs/my-file.md in version name=1.0.0
```

This information is critical for quickly identifying which file needs to be fixed, especially in large documentation sites with hundreds of files.

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
