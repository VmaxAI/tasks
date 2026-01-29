# Bug Report

### Describe the bug

After a recent update, versioned sidebars are not being loaded correctly. The plugin is looking for sidebar files in the wrong directory path and with an incorrect filename pattern.

### Reproduction

```js
// Plugin configuration
{
  id: 'custom-docs',
  // ... other options
}
```

When building the site with a custom plugin ID and versioned docs, the sidebar files are not found. The plugin appears to be constructing the path incorrectly.

Expected file path: `versioned_sidebars/version-1.0.0-sidebars.json`
Actual path being searched: Different location with wrong naming pattern

### Expected behavior

The plugin should correctly locate versioned sidebar files using the proper directory structure and filename convention. Versioned sidebars should load without errors.

### System Info
- Docusaurus version: Latest
- Node version: 18.x

---
Repository: /testbed
