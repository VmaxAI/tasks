# Bug Report

### Describe the bug

I'm experiencing an issue where duplicate command names are not being detected properly. When I try to add a command with the same name as an existing command, it doesn't throw an error like it should. Instead, both commands get registered and the program behaves unexpectedly.

### Reproduction

```js
const program = new Command();

program
  .command('deploy')
  .description('Deploy the application');

// This should throw an error but doesn't
program
  .command('deploy')
  .description('Deploy with different options');

// Both commands appear to be registered
```

### Expected behavior

When attempting to register a command with a name or alias that already exists, the library should throw an error with a message like:
```
cannot add command 'deploy' as already have command 'deploy'
```

This validation worked correctly in previous versions but seems to have stopped working recently.

### System Info
- Node version: v18.x
- Commander.js: latest

---
Repository: /testbed
