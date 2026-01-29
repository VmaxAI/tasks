# Bug Report

### Describe the bug

The order of documents in the global data appears to be incorrect. When using the docs plugin, category-generated index pages are now appearing before regular docs in the `docs` array, which breaks assumptions about document ordering.

### Reproduction

```js
// Expected order: regular docs first, then generated indices
// Actual order: generated indices first, then regular docs

const version = {
  docs: [
    { id: 'doc1', title: 'Doc 1' },
    { id: 'doc2', title: 'Doc 2' }
  ],
  categoryGeneratedIndices: [
    { id: 'category-index', title: 'Category' }
  ]
}

// After processing, the docs array has:
// ['category-index', 'doc1', 'doc2']
// But it should be:
// ['doc1', 'doc2', 'category-index']
```

### Expected behavior

Regular documentation pages should appear before category-generated index pages in the global data structure. The current ordering breaks compatibility with code that expects docs to be listed first.

Also noticing that `draftIds` seems to only include IDs from `version.docs` but not from `version.drafts` - not sure if this is related or a separate issue.

### System Info
- Docusaurus version: latest
- Plugin: @docusaurus/plugin-content-docs

---
Repository: /testbed
