# Bug Report

### Describe the bug

After a recent update, I'm experiencing a critical issue where effect scopes stop working entirely. When trying to run functions within an effect scope using the `run()` method, nothing happens - the function doesn't execute at all.

### Reproduction

```js
import { effectScope } from 'vue'

const scope = effectScope()

const result = scope.run(() => {
  console.log('This should execute')
  return 'test value'
})

console.log(result) // Expected: 'test value', Actual: undefined
```

### Expected behavior

The function passed to `scope.run()` should execute and return its result. In the example above, it should log "This should execute" to the console and `result` should be `'test value'`.

### Additional context

This seems to affect all effect scopes, not just specific cases. The scope appears to be active (not stopped), but the `run()` method simply doesn't execute the callback function anymore.

---
Repository: /testbed
