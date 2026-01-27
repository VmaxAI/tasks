# Bug Report

### Describe the bug

I'm experiencing an issue with custom argument parsers where the parser function doesn't receive the expected arguments. When I define a custom parser using `argParser()`, the function is called but the value being parsed isn't passed to it.

### Reproduction

```js
program
  .argument('<value>', 'A value to parse')
  .argParser((val) => {
    console.log('Received:', val); // Expected: the actual value, Actual: undefined
    return parseInt(val);
  })
  .action((parsedValue) => {
    console.log('Parsed:', parsedValue);
  });

program.parse(['node', 'script.js', '42']);
```

### Expected behavior

The parser function should receive the argument value as a parameter so it can transform/validate it. In the example above, `val` should be `'42'` (the string passed on the command line), and the parser should be able to convert it to the number `42`.

### Actual behavior

The parser function is called but doesn't receive any arguments. `val` is `undefined`, which causes the parsing logic to fail.

This seems to have broken recently - custom argument parsers were working fine before. Not sure if this is related to a recent change or if I'm missing something in how the API is supposed to work.

---
Repository: /testbed
