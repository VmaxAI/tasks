# Bug Report

### Describe the bug

When registering multiple hooks for the same lifecycle event using `.hook()`, only the first hook gets executed. Subsequent hooks registered for the same event are ignored and don't run.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

let firstHookCalled = false;
let secondHookCalled = false;

program
  .hook('preAction', () => {
    firstHookCalled = true;
    console.log('First hook executed');
  })
  .hook('preAction', () => {
    secondHookCalled = true;
    console.log('Second hook executed');
  });

program
  .action(() => {
    console.log('Action executed');
  });

program.parse(['node', 'test']);

// Expected: both hooks should be called
// Actual: only the first hook is called
console.log('First hook called:', firstHookCalled);  // true
console.log('Second hook called:', secondHookCalled); // false (should be true)
```

### Expected behavior

All hooks registered for the same lifecycle event should be executed in the order they were registered. When calling `.hook('preAction', callback)` multiple times, each callback should be added to the list of hooks and executed.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
