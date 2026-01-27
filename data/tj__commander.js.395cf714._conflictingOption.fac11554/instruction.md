# Bug Report

### Describe the bug

When using conflicting options with boolean flags, the error message shows the wrong option name. Instead of displaying which option is actually conflicting, it displays the same option twice in the error message.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('--foo')
  .option('--bar')
  .conflictsWith('foo', 'bar');

// Try using both conflicting options
program.parse(['node', 'test', '--foo', '--bar']);
```

The error message shows something like:
```
error: option '--bar' cannot be used with option '--bar'
```

Instead of the expected:
```
error: option '--foo' cannot be used with option '--bar'
```

### Expected behavior

The error message should correctly identify both conflicting options - showing which option was used that conflicts with which other option. Currently it seems to be displaying the same option name twice instead of showing both conflicting options.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
