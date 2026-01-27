# Bug Report

### Describe the bug

After a recent update, I'm getting a syntax error when trying to use `effectScope().run()`. The application fails to compile/run and throws an error about unexpected indentation or invalid syntax.

### Reproduction

```js
import { effectScope } from 'vue'

const scope = effectScope()

scope.run(() => {
  // Some reactive logic here
  console.log('Running in scope')
})
```

### Expected behavior

The code should execute normally without any syntax errors. The `run()` method should execute the provided callback function within the effect scope context.

### System Info
- Vue version: 3.x
- Node version: 18.x

This seems to have broken after pulling the latest changes. The error appears to be coming from the reactivity package itself rather than my application code.

---
Repository: /testbed
