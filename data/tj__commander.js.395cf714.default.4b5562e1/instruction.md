# Bug Report

### Describe the bug

I'm experiencing an issue with the `default()` method on Option objects. When I call `default()` with just a value (no description), the method doesn't return the Option instance, breaking method chaining.

### Reproduction

```js
const { Option } = require('commander');

const option = new Option('-p, --port <number>', 'port number');

// This breaks - option2 is undefined
const option2 = option.default(3000);

// Can't chain further methods
option2.argParser(parseInt); // TypeError: Cannot read property 'argParser' of undefined
```

### Expected behavior

The `default()` method should always return the Option instance to allow method chaining, regardless of whether a description is provided or not.

```js
// This should work
const option = new Option('-p, --port <number>', 'port number')
  .default(3000)
  .argParser(parseInt);
```

### System Info
- commander version: latest
- Node.js version: 18.x

This seems to have started happening recently. The method used to always return `this` for chaining.

---
Repository: /testbed
