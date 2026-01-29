# Bug Report

### Describe the bug

Error messages are missing critical information when processing doc metadata fails. The error message no longer includes the file path of the problematic document, making it extremely difficult to debug which file is causing the issue.

### Reproduction

1. Create a doc file with invalid metadata or content that causes processing to fail
2. Build the site
3. Observe the error message

The error now shows:
```
Can't process doc metadata for doc at path path= in version name=1.0.0
```

Instead of showing which file actually failed.

### Expected behavior

The error message should include the full file path of the document that failed to process, like:
```
Can't process doc metadata for doc at path path=docs/my-problematic-doc.md in version name=1.0.0
```

This information is crucial for debugging, especially in large documentation sites with hundreds of files.

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
