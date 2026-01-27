# Bug Report

### Describe the bug

I'm experiencing an issue with the `arguments()` method where it's not parsing argument definitions correctly. When I define multiple arguments separated by spaces, they get split in an unexpected way and the individual arguments are not being recognized properly.

### Reproduction

```js
const program = new Command();

program
  .arguments('<source> <destination>')
  .action((source, destination) => {
    console.log('source:', source);
    console.log('destination:', destination);
  });

program.parse(['node', 'script.js', 'file1.txt', 'file2.txt']);
```

When running this code, the arguments are not being parsed as expected. It seems like the splitting behavior has changed and is now treating each character differently instead of properly separating by spaces.

### Expected behavior

The `arguments()` method should correctly parse space-separated argument definitions like `'<source> <destination>'` and create two separate arguments. Each argument should be properly registered and accessible in the action callback.

### System Info
- Node version: 16.x
- OS: macOS

---
Repository: /testbed
