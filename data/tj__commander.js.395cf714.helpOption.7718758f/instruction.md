# Bug Report

### Describe the bug

When customizing the help option using `helpOption()` with custom flags or description, I'm getting an error because the code tries to initialize the option group before the help option is actually created.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// This throws an error
program.helpOption('-h, --help', 'show help information');

program.parse();
```

The error occurs because `_initOptionGroup()` is being called with `this._helpOption` before it's assigned the newly created option.

### Expected behavior

The help option should be created successfully with custom flags and description without any errors. The option group initialization should happen after the help option is created.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
