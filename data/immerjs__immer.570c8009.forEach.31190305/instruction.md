# Bug Report

### Describe the bug

After updating to the latest version, I'm getting a syntax error when trying to use `Set` with reactive objects. The application fails to load and throws an error about unexpected token.

### Reproduction

```js
import { enableMapSet } from './plugins/mapset'

enableMapSet()

const mySet = new Set([1, 2, 3])

mySet.forEach((value) => {
  console.log(value)
})
```

### Expected behavior

The `forEach` method should iterate over all values in the Set and print them to the console. The code should run without any syntax errors.

### Additional context

This was working fine in the previous version. After pulling the latest changes, the application won't even start. It looks like there might be an issue with the `forEach` implementation in the mapset plugin - the error points to that file but I can't figure out what's wrong.

---
Repository: /testbed
