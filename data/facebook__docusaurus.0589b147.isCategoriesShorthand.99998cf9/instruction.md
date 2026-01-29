# Bug Report

### Describe the bug

I'm experiencing an issue with sidebar category shorthand detection in Docusaurus. When I try to use the object shorthand syntax for sidebar categories (without explicitly specifying a `type` field), they are not being recognized correctly and the sidebar structure breaks.

### Reproduction

```js
// sidebars.js
module.exports = {
  docs: [
    {
      'Getting Started': ['intro', 'installation'],
      'Guides': ['guide1', 'guide2']
    }
  ]
}
```

When using this shorthand syntax (which should be valid according to the docs), the sidebar doesn't render properly. It seems like the category shorthand is not being detected as expected.

### Expected behavior

The shorthand syntax should be recognized and the sidebar should render with proper category structure. Categories defined using the object shorthand notation (without an explicit `type` field) should work the same way as categories with `type: 'category'` explicitly set.

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
