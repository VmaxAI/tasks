# Bug Report

### Describe the bug

After a recent update, I'm getting a syntax error when trying to use the MDX parser. The module seems to have an issue with its exports - specifically there's a malformed export statement that's preventing the code from running at all.

### Reproduction

```js
import { text } from '@mdx-js/mdx';

// Throws a syntax error before any code can execute
```

The error appears to be in the constructs exports section of the vendored MDX file. When trying to import or use any MDX functionality, the JavaScript engine fails to parse the module due to what looks like a corrupted export declaration.

### Expected behavior

The MDX module should load without syntax errors and allow normal usage of its exported functions and constructs.

### Additional context

This seems to have started happening after the latest changes. The module was working fine before, but now it fails immediately on load. Looking at the error, it appears there's a missing identifier in one of the export statements in the constructs_exports section.

---
Repository: /testbed
