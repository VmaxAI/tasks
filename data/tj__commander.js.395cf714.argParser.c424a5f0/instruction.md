# Bug Report

### Describe the bug

The `argParser()` method on `Option` is not working as expected. When I set a custom argument parser function, it doesn't receive the command-line argument value that should be passed to it. The parser function is being called without any arguments, making it impossible to actually parse the input.

### Reproduction

```js
const { Option } = require('commander');

const option = new Option('-p, --port <number>', 'port number');

option.argParser((value) => {
  console.log('Received value:', value); // value is undefined!
  return parseInt(value);
});

// When parsing command line arguments like: --port 3000
// The parser function gets called but 'value' is undefined
```

### Expected behavior

The custom parser function should receive the command-line argument value as a parameter so it can transform/validate it. For example, if the user provides `--port 3000`, the parser should receive `'3000'` as the value argument.

Currently the parser is called without any arguments, so there's no way to access the actual value that needs to be parsed.

### Additional context

This seems to have broken recently. The method signature suggests it should work like other argument parsers where the value is passed in, but something is preventing the argument from being forwarded correctly.

---
Repository: /testbed
