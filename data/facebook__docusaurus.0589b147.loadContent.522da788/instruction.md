# Bug Report

### Describe the bug

When a docs version has no documents, the error message shows an incorrect path. The error points to a non-existent directory instead of the actual localized content path where docs should be placed.

### Reproduction

1. Create a versioned docs setup with localization enabled
2. Create a version that has no docs in the localized content path
3. Try to build the site

The error message will show:
```
Docs version "X" has no docs! At least one doc should exist at "docs"
```

But the actual path where docs are expected is the localized path (e.g., `i18n/fr/docusaurus-plugin-content-docs/version-X`)

### Expected behavior

The error message should point to the correct localized content path where the docs are actually expected to be found, making it easier to understand where to add the missing documentation.

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
