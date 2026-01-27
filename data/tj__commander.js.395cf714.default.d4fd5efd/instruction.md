# Bug Report

### Describe the bug

I'm having an issue with the `default()` method on arguments. When I chain multiple method calls after setting a default value, the chain breaks and I get a TypeError saying the next method is not a function.

### Reproduction

```js
const { Argument } = require('commander');

const arg = new Argument('<value>', 'some value')
  .default('test', 'default description')
  .choices(['a', 'b', 'c']);  // TypeError: .choices is not a function
```

This used to work fine before, but now the chaining is broken. It seems like `default()` is not returning the Argument instance anymore.

### Expected behavior

The `default()` method should return the Argument instance to allow method chaining, just like other methods in the API. Something like:

```js
const arg = new Argument('<value>', 'some value')
  .default('test', 'default description')
  .choices(['a', 'b', 'c'])
  .argParser(customParser);
```

All these calls should chain properly without throwing errors.

### System Info
- commander version: latest
- Node version: 18.x

---
Repository: /testbed
