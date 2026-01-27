# Bug Report

### Describe the bug

I'm experiencing an issue with chained asynchronous operations in commander.js. When using async hooks or actions that return promises, the execution order seems incorrect - subsequent operations are being called before the previous promise resolves.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .hook('preAction', async () => {
    console.log('Starting async operation...');
    await new Promise(resolve => setTimeout(resolve, 1000));
    console.log('Async operation completed');
  })
  .action(() => {
    console.log('Action executed');
  });

program.parse();
```

### Expected behavior

The output should be:
```
Starting async operation...
Async operation completed
Action executed
```

### Actual behavior

The action executes immediately without waiting for the async hook to complete:
```
Starting async operation...
Action executed
Async operation completed
```

This breaks the expected flow when you need to perform async setup operations (like loading config, connecting to database, etc.) before the main action runs.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
