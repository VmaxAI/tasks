# Bug Report

### Describe the bug

I'm experiencing an issue with the auto-generated sidebars where document IDs are being processed incorrectly. It seems like the logic for extracting the local document ID is not working as expected.

When I have documents with paths like `guides/tutorial/getting-started`, the sidebar generation is producing unexpected results. The document references in the generated sidebar don't match what I'd expect based on the file structure.

### Reproduction

Given a docs structure like:
```
docs/
  guides/
    tutorial/
      getting-started.md
```

With a document ID like `guides/tutorial/getting-started`, the sidebar auto-generation doesn't seem to be handling the ID correctly. The resulting sidebar structure shows incorrect document references.

### Expected behavior

The auto-generated sidebar should correctly extract and use the appropriate part of the document ID to create proper sidebar items. Documents should be referenced correctly regardless of their path depth.

### System Info
- Docusaurus version: latest
- Node version: 18.x

This might be related to how the document IDs are being parsed internally. Any help would be appreciated!

---
Repository: /testbed
