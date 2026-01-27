# Bug Report

### Describe the bug

I'm experiencing an issue with option creation where the flags and description parameters appear to be swapped. When I create a custom option using `createOption()`, the option object has its flags and description reversed from what I passed in.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

const option = program.createOption('-d, --debug', 'enable debug mode');

// The option has description where flags should be and vice versa
console.log(option.flags); // Expected: '-d, --debug', but shows 'enable debug mode'
console.log(option.description); // Expected: 'enable debug mode', but shows '-d, --debug'
```

### Expected behavior

The `createOption()` method should preserve the order of parameters - flags should be stored as flags, and description should be stored as description. The created option object should have the correct values in the correct properties.

### System Info
- commander version: latest
- Node version: v18.x

---
Repository: /testbed
