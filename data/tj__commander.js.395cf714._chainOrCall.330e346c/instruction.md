# Bug Report

### Describe the bug

When chaining async hooks/actions, the execution order seems incorrect. The callback function is being executed immediately instead of waiting for the promise to resolve first. This breaks the expected sequential execution of async operations.

### Reproduction

```js
const program = new Command();

let executionOrder = [];

program
  .hook('preAction', async () => {
    executionOrder.push('hook-start');
    await new Promise(resolve => setTimeout(resolve, 100));
    executionOrder.push('hook-end');
  })
  .action(() => {
    executionOrder.push('action');
  });

await program.parseAsync(['node', 'test']);

console.log(executionOrder);
// Expected: ['hook-start', 'hook-end', 'action']
// Actual: ['hook-start', 'action', 'hook-end']
```

### Expected behavior

When a hook returns a promise, the next callback should only execute after the promise resolves. The execution should be sequential, not parallel.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
