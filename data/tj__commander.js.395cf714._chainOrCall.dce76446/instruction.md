# Bug Report

### Describe the bug

I'm experiencing an issue with command chaining when using async hooks. When I have a hook that returns a promise, the next hook in the chain doesn't execute properly - it seems like the promise handling is broken.

### Reproduction

```js
program
  .hook('preAction', async (thisCommand, actionCommand) => {
    await someAsyncOperation();
    console.log('First hook completed');
  })
  .hook('preAction', (thisCommand, actionCommand) => {
    console.log('Second hook should run after first');
  });

program.parse();
```

### Expected behavior

When the first hook returns a promise, the second hook should wait for it to complete before executing. The hooks should run in sequence, with the second hook only starting after the first one finishes.

Currently, the second hook either doesn't run at all or the promise chain seems to be broken somehow.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
