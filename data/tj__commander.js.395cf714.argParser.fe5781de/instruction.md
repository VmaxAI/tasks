# Bug Report

### Describe the bug

The `argParser()` method is behaving unexpectedly - it seems to be calling the parser function immediately with the Argument instance instead of just storing it for later use. This causes the parser function to execute at definition time rather than when the argument is actually being parsed.

### Reproduction

```js
const { Argument } = require('commander');

const arg = new Argument('<value>', 'test argument')
  .argParser((value) => {
    console.log('Parsing:', value);
    return parseInt(value);
  });

// The parser function gets called immediately with the Argument instance
// Expected: parser should only be called when parsing actual argument values
```

When defining an argument with a custom parser, the parser function is invoked right away with the Argument object instead of being stored for later use during argument parsing.

### Expected behavior

The `argParser()` method should store the parser function and only invoke it later when actual argument values need to be parsed. The parser should receive the argument value (string) as input, not the Argument instance.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
