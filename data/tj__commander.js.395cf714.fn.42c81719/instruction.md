# Bug Report

### Describe the bug

I'm experiencing an issue with option parsing when using a RegExp as a custom argument parser. When the regex matches, the parsed value is not being extracted correctly from the match result.

### Reproduction

```js
const program = new Command();

program
  .option('-p, --port <number>', 'port number', /^\d+$/)
  .parse(['node', 'test', '--port', '3000']);

console.log(program.opts().port);
// Expected: '3000'
// Actual: undefined (or default value if set)
```

The regex matches successfully, but the value doesn't get assigned to the option. It seems like the matched value isn't being returned properly from the parser function.

### Expected behavior

When a RegExp is provided as the custom argument parser and it matches the input, the matched value should be returned and assigned to the option. If the regex doesn't match, the default value should be used.

### System Info
- Node version: 18.x
- commander version: latest

---
Repository: /testbed
