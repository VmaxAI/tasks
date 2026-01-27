# Bug Report

### Describe the bug

After upgrading to the latest version, the `createOption()` method is returning unexpected data. Instead of returning just the Option object, it now returns an object with `option`, `flags`, and `description` properties, and the `flags` and `description` values appear to be swapped or incorrectly assigned.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

const option = program.createOption('-p, --port <number>', 'port number');

console.log(option);
// Expected: Option object
// Actual: { option: Option {...}, flags: '-p,', description: '-p, --port <number>' }
```

When trying to use the returned value as an Option object directly, it fails because the structure has changed completely.

### Expected behavior

`createOption()` should return a plain Option instance like it did before, not a wrapper object with mixed up properties. The flags and description parameters should be passed correctly to the Option constructor without being swapped.

### System Info
- commander version: latest
- Node.js version: 18.x

This is breaking existing code that relies on `createOption()` returning an Option object directly.

---
Repository: /testbed
