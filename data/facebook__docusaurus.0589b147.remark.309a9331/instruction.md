# Bug Report

### Describe the bug

After a recent update, I'm getting `TypeError: remark is not a function` when trying to use the remark module. It seems like the export is no longer functioning correctly.

### Reproduction

```js
const { remark } = require('remark');

// This now throws: TypeError: remark is not a function
const processor = remark();
```

### Expected behavior

The `remark` export should be a function that can be called to create a processor instance, just like it was before the update.

### System Info
- remark version: 15.0.1
- Node version: Latest

---
Repository: /testbed
