# Bug Report

### Describe the bug

After a recent update, I'm unable to access documents by their ID in the docs plugin. It seems like the document lookup is broken - when I try to reference a document by its ID, I get undefined or the wrong document.

### Reproduction

```js
// In my custom component
const docById = versionDocs['my-doc-id'];
console.log(docById); // Returns undefined or wrong document

// The document with id 'my-doc-id' exists but can't be accessed
```

This is breaking my custom components that rely on looking up documents by their ID from the `versionDocs` object.

### Expected behavior

Documents should be accessible by their ID in the `versionDocs` prop, just like before. The object should be keyed by document IDs, not titles.

### System Info
- Docusaurus version: Latest
- Node version: 18.x

---
Repository: /testbed
