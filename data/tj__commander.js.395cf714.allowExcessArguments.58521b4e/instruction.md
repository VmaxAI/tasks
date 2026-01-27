# Bug Report

### Describe the bug

The `allowExcessArguments()` method is not working as expected. When I call this method to enable excess arguments, it seems to have no effect and excess arguments are still being rejected by the command parser.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .name('test')
  .argument('<required>')
  .allowExcessArguments(true)
  .action((required, ...args) => {
    console.log('Required:', required);
    console.log('Extra args:', args);
  });

// Try parsing with excess arguments
program.parse(['node', 'test.js', 'value1', 'value2', 'value3']);
```

### Expected behavior

When `allowExcessArguments(true)` is called, the command should accept extra arguments beyond what's defined. The method should also return the command instance for method chaining.

Currently it appears that:
1. Excess arguments are always rejected regardless of the setting
2. Method chaining doesn't work properly after calling this method

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
