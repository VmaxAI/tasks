# Bug Report

### Describe the bug

When adding documents to the sidebar configuration, I'm getting an error saying the document ID cannot be found, even though the document definitely exists in my docs folder. This seems to be happening for all valid document IDs.

### Reproduction

1. Create a valid document in your docs folder (e.g., `docs/intro.md`)
2. Add it to your sidebar configuration:

```js
module.exports = {
  mySidebar: [
    {
      type: 'doc',
      id: 'intro',
    },
  ],
};
```

3. Build or start the dev server
4. You'll get an error like:

```
Invalid sidebars file. The document with id "intro" was used in the sidebar, but no document with this id could be found.
Available document ids are:
intro
getting-started
tutorial
...
```

### Expected behavior

The sidebar should load correctly when referencing valid document IDs. The document clearly exists (it's even listed in the "Available document ids" in the error message), so it should work without throwing an error.

### System Info

- Docusaurus version: latest
- Node version: 18.x

This is blocking me from building my documentation site. Any help would be appreciated!

---
Repository: /testbed
