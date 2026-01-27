# Bug Report

### Describe the bug

When registering multiple hooks of the same type using `.hook()`, only the first hook gets executed. Subsequent hooks registered for the same event are ignored and don't run.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

let firstHookCalled = false;
let secondHookCalled = false;

program
  .hook('preAction', () => {
    firstHookCalled = true;
    console.log('First hook called');
  })
  .hook('preAction', () => {
    secondHookCalled = true;
    console.log('Second hook called');
  });

program.parse();

// Expected: both hooks should be called
// Actual: only the first hook is called
console.log('First hook:', firstHookCalled);  // true
console.log('Second hook:', secondHookCalled); // false - this should be true!
```

### Expected behavior

When multiple hooks are registered for the same event (e.g., 'preAction'), all of them should be executed in the order they were registered. Currently, only the first hook runs and subsequent hooks are silently ignored.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
