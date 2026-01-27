# Bug Report

### Describe the bug

After calling `argRequired()` on an argument, subsequent method calls don't seem to work properly. It looks like the method is returning a new object instead of modifying the existing instance, which breaks method chaining and causes the argument configuration to be lost.

### Reproduction

```js
const { Argument } = require('commander');

const arg = new Argument('<file>', 'file to process');
arg.argRequired().default('input.txt');

// The argument doesn't behave as expected
// The required flag seems to be set on a different object
// and the default value is set on the original instance
```

### Expected behavior

The `argRequired()` method should modify the current instance and return `this` to allow proper method chaining. All subsequent method calls should work on the same argument instance with the required flag properly set.

### System Info
- commander version: latest
- Node.js version: v18.x

---
Repository: /testbed
