# Bug Report

### Describe the bug

When using versioned docs, the version label translation is not working correctly. The translation file lookup appears to be using the wrong property, which causes the version label to fallback to an incorrect value when translations are provided.

### Reproduction

1. Set up a Docusaurus site with versioned docs
2. Configure a version with a custom `label` that differs from `versionName`
3. Add translation files for the version using the version's label
4. The translation file won't be found correctly, and the fallback value will be wrong

Example configuration:
```js
{
  versionName: '1.0.0',
  label: 'Version 1.0'
}
```

When translations are provided, the system tries to look up the translation file using `version.label` but should use `version.versionName`. Additionally, when no translation is found, it falls back to `version.label` instead of `version.versionName`, causing the wrong value to be displayed.

### Expected behavior

- Translation files should be looked up using `versionName` 
- When no translation is available, the fallback should be `versionName` not `label`
- Version labels should display correctly with or without translations

### System Info

- Docusaurus version: Latest
- Plugin: @docusaurus/plugin-content-docs

---
Repository: /testbed
