# Bug Report

### Describe the bug

I'm experiencing an issue where option values are being shared across multiple parse calls when reusing a command instance. After the first parse, subsequent parses seem to retain values from previous parses instead of resetting to their defaults.

### Reproduction

```js
const program = new Command();
program
  .option('-n, --name <name>', 'name', 'default-name')
  .option('-v, --verbose', 'verbose mode');

// First parse
program.parse(['node', 'test', '--name', 'first', '--verbose']);
console.log(program.opts()); // { name: 'first', verbose: true }

// Second parse - should reset to defaults
program.parse(['node', 'test']);
console.log(program.opts()); // Expected: { name: 'default-name', verbose: false }
                              // Actual: { name: 'first', verbose: true }
```

### Expected behavior

Each call to `parse()` should start with a clean slate, with option values reset to their defaults. Options from previous parse calls should not persist.

### System Info
- commander version: latest
- Node.js version: v18.x

This seems to have started happening recently. The state restoration between parse calls doesn't appear to be working correctly anymore.

---
Repository: /testbed
