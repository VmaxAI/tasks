# Bug Report

### Describe the bug

I'm experiencing an issue with chained async actions where the result from the previous action isn't being passed to the next one in the chain. The actions execute in sequence, but each action seems to start with `undefined` instead of receiving the return value from the previous action.

### Reproduction

```js
command
  .action(async () => {
    return { userId: 123 };
  })
  .action(async (result) => {
    console.log(result); // Expected: { userId: 123 }, Actual: undefined
    return result;
  });
```

When chaining multiple actions together, I expect the return value from one action to be passed as an argument to the next action in the chain. However, the subsequent actions are receiving `undefined` instead.

### Expected behavior

The return value from each action should be passed to the next action in the chain, allowing data to flow through the action pipeline.

### System Info
- Node version: 18.x
- Package version: latest

---
Repository: /testbed
