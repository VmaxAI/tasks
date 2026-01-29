# Bug Report

### Describe the bug

I'm experiencing an issue with sidebar translations in the docs plugin. It seems like translatable sidebar items are being filtered out instead of being included in the translation file. This causes documents that should be translatable to not appear in the generated translation files.

### Reproduction

1. Set up a docs plugin with a sidebar containing translatable doc items
2. Mark some sidebar items as `translatable: true`
3. Generate translation files
4. The translatable items are missing from the output

Example sidebar configuration:
```js
{
  type: 'doc',
  id: 'intro',
  label: 'Introduction',
  translatable: true
}
```

### Expected behavior

Items marked as `translatable: true` should be included in the translation file content so they can be translated. Currently it appears the logic is inverted - only non-translatable items are being included.

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
