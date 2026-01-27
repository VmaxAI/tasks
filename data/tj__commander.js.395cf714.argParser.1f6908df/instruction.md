# Bug Report

### Describe the bug

The `argParser()` method is not working as expected. When I set a custom argument parser function and then try to use it, the behavior is completely broken.

### Reproduction

```js
const { Option } = require('commander');

const option = new Option('-p, --port <number>', 'port number');

// Set custom parser
option.argParser((value) => {
  return parseInt(value, 10);
});

// Try to use the option
// The parseArg function doesn't work correctly anymore
```

When calling `argParser()`, it seems like the method is returning something unexpected instead of the Option instance itself, breaking method chaining. Also, the parser function I provide doesn't get called with the correct arguments when the option is actually parsed.

### Expected behavior

1. `argParser()` should return the Option instance to allow method chaining
2. The custom parser function should be stored and called with the argument value when parsing

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
