# Bug Report

### Describe the bug

The `addHelpOption` method appears to be completely broken or missing. When trying to customize the help option in my CLI application, I'm getting errors that the method doesn't exist or isn't functioning properly.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

const customHelpOption = new Option('-h, --help', 'display custom help');
program.addHelpOption(customHelpOption);

// Trying to use the command results in unexpected behavior
```

### Expected behavior

The `addHelpOption` method should allow customizing the help option for the command. It should accept an Option object and properly register it with the command instance.

### System Info
- commander.js version: latest
- Node.js version: 18.x

This seems to have broken recently - the method was working fine before. Not sure what happened but it's blocking my project from working correctly.

---
Repository: /testbed
