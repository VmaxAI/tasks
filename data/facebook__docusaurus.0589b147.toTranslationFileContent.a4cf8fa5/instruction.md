# Bug Report

### Describe the bug

I'm experiencing an issue with translation extraction where some translations from source code files are being skipped. It appears that the first file's translations are not being included in the final extracted translations output.

### Reproduction

Given multiple source code files with translations:

**file1.js:**
```js
translate({
  id: 'homepage.title',
  message: 'Welcome'
})
```

**file2.js:**
```js
translate({
  id: 'about.title',
  message: 'About Us'
})
```

When extracting translations, only the translations from `file2.js` (and subsequent files) are included in the output. The translations from the first file are missing from the final translation file.

### Expected behavior

All translations from all source code files should be extracted and merged into the translation output file. The translation with id `homepage.title` from the first file should be present in the extracted translations.

### System Info
- Docusaurus version: latest
- Node version: 18.x

This seems to have started recently. Not sure if this is related to a recent change in how translations are being aggregated from multiple files.

---
Repository: /testbed
