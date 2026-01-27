# Bug Report

### Describe the bug

Getting a runtime error when trying to register a hook on a command instance. The error says "Cannot read property 'push' of undefined" when calling the `hook()` method.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// This throws an error
program.hook('preAction', () => {
  console.log('Before action');
});

program
  .command('test')
  .action(() => {
    console.log('Running test');
  });

program.parse();
```

### Expected behavior

The hook should be registered successfully without throwing an error. The callback should be stored and executed at the appropriate lifecycle event.

### Additional context

This seems to happen on the first hook registration for any event type. If I try to register multiple hooks for the same event, only the first one fails.

---
Repository: /testbed
