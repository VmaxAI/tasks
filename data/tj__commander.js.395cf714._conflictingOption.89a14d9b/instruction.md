# Bug Report

### Describe the bug

When using conflicting options with the `.conflicts()` method, the error message shows incorrect option names. Both parts of the error message display the same conflicting option instead of showing which two options are actually conflicting with each other.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-a, --alpha', 'alpha option')
  .option('-b, --beta', 'beta option')
  .conflictOption('alpha', 'beta');

program.parse(['node', 'test', '--alpha', '--beta']);
```

When running this with both conflicting options, the error message incorrectly displays the same option twice instead of showing both the source option and the conflicting option.

### Expected behavior

The error message should clearly indicate which two options are in conflict, for example:
```
error: option '--alpha' cannot be used with option '--beta'
```

Instead, it currently shows something like:
```
error: option '--beta' cannot be used with option '--beta'
```

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
