# Bug Report

### Describe the bug

The `createOption` function is not working correctly - options created with it have their flags and description swapped internally. This causes issues when trying to use the created options with commands.

### Reproduction

```js
const { createOption } = require('commander');

const option = createOption('-p, --port <number>', 'port number');

// The option is created but flags and description are in wrong positions
console.log(option.flags); // Expected: '-p, --port <number>'
console.log(option.description); // Expected: 'port number'
```

When using this option with a command, the help text shows incorrect information and option parsing may fail.

### Expected behavior

The `createOption` function should correctly assign the flags parameter to the flags property and the description parameter to the description property, matching the behavior of creating an Option directly with `new Option(flags, description)`.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
