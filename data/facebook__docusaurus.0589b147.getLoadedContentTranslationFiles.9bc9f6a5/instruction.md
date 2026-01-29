# Bug Report

### Describe the bug

After a recent update, the docs plugin seems to be filtering out all translation files. When building the site, none of the translation files are being loaded or processed, causing the entire translation system to fail silently.

### Reproduction

```js
const loadedContent = {
  loadedVersions: [
    // ... version data with translation files
  ]
};

const files = getLoadedContentTranslationFiles(loadedContent);
console.log(files); // Returns empty array []
```

### Expected behavior

The function should return all valid translation files from the loaded versions. Previously this was working fine and all translation files were being included in the build.

### System Info
- Docusaurus version: Latest
- Node version: 18.x

This is blocking our internationalization setup completely. Any help would be appreciated!

---
Repository: /testbed
