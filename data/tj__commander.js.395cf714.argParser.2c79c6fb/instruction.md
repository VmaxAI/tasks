# Bug Report

### Describe the bug

I'm experiencing an issue with custom argument parsers where the parsed value is not being returned correctly. When I use `.argParser()` to define a custom parser function for an option, the parsed value seems to get lost and the option value becomes `undefined`.

### Reproduction

```js
program
  .option('-p, --port <number>', 'port number')
  .argParser((value) => {
    return parseInt(value, 10);
  });

program.parse(['node', 'test', '--port', '3000']);

console.log(program.opts().port);
// Expected: 3000
// Actual: undefined
```

The custom parser function executes, but the return value doesn't get assigned to the option. This breaks any custom parsing logic that needs to transform the input value.

### Expected behavior

The value returned from the custom argument parser function should be set as the option's value. In the example above, `program.opts().port` should equal `3000` (as a number), not `undefined`.

### System Info
- Node version: 18.x
- OS: macOS

---
Repository: /testbed
