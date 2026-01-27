# Bug Report

### Describe the bug

I'm having trouble with custom argument parsers on options. When I provide a parser function using `argParser()`, it seems like the function is being called without the expected arguments. The parser receives no parameters even though I'm expecting it to get the value that needs to be parsed.

### Reproduction

```js
program
  .option('-p, --port <number>', 'port number')
  .argParser((value) => {
    console.log('Received value:', value); // prints: Received value: undefined
    return parseInt(value);
  });

program.parse(['node', 'script.js', '--port', '3000']);
```

### Expected behavior

The `argParser` function should receive the string value `'3000'` as its argument so it can parse and transform it. Instead, it appears to be called with no arguments at all.

### System Info
- Node version: 18.x
- OS: Linux

---
Repository: /testbed
