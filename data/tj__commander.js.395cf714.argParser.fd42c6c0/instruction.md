# Bug Report

### Describe the bug

I'm having an issue with the `argParser()` method. When I try to set a custom argument parser function, it seems like the function is being called immediately instead of being stored for later use. This breaks the argument parsing functionality.

### Reproduction

```js
const { Argument } = require('commander');

const arg = new Argument('<value>', 'A value');

// Try to set a custom parser
arg.argParser((value) => {
  return parseInt(value, 10);
});

// Later when parsing...
// The parser function is not available anymore
```

When I call `argParser()` with a function, it appears to execute the function right away rather than saving it for when the argument actually needs to be parsed. The method also seems to return something unexpected instead of the `Argument` instance for chaining.

### Expected behavior

The `argParser()` method should:
1. Store the provided function for later use when parsing arguments
2. Return the `Argument` instance to allow method chaining
3. Not execute the parser function until an actual argument value needs to be parsed

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
