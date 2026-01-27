# Bug Report

### Describe the bug

I'm experiencing an issue where error messages are not being displayed correctly. Instead of showing the actual error text, the output shows something like `[Function: baseWrite]` or similar function representation when errors occur.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('-n, --number <value>', 'a number', parseInt)
  .action((options) => {
    console.log('options:', options);
  });

// Try to parse with an invalid value that will trigger an error
program.parse(['node', 'test', '--number', 'not-a-number']);
```

When the parsing fails, the error output is broken and shows the function itself instead of the error message.

### Expected behavior

Error messages should be displayed as readable text, not as function representations. For example, when providing an invalid argument, I should see a proper error message explaining what went wrong.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
