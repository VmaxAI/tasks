# Bug Report

### Describe the bug

I'm getting an error when trying to use valid sidebar configurations in my Docusaurus site. The plugin is throwing an "Invalid sidebar items collection" error for configurations that should be perfectly valid according to the documentation.

### Reproduction

```js
// sidebars.js
module.exports = {
  docs: [
    {
      type: 'category',
      label: 'Getting Started',
      items: ['intro', 'installation'],
    },
    'api-reference',
  ],
};
```

When I run the build, I get an error message saying the sidebar items collection is invalid, even though this is a standard array-based sidebar configuration.

### Expected behavior

The sidebar configuration should be accepted and processed normally. Array-based sidebar configurations are documented as valid and have worked in previous versions.

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
