# Bug Report

### Describe the bug

When using the `argument()` method with a custom parser function and default value, the parameters seem to be swapped. The parser function is being treated as the default value and the default value is being treated as the parser.

### Reproduction

```js
program
  .argument('<input>', 'input file', (value) => {
    return value.toUpperCase();
  }, 'default.txt');
```

In this case, the parser function should transform the input to uppercase, and if no argument is provided, it should use 'default.txt' as the default value. However, the behavior is reversed - the function is being used as the default and the string is being used as the parser.

### Expected behavior

When calling `.argument(name, description, parseArg, defaultValue)`:
- The third parameter (`parseArg`) should be used as the argument parser function
- The fourth parameter (`defaultValue`) should be used as the default value when no argument is provided

The parser should be applied to transform the input value, and the default should be returned when the argument is not specified.

### System Info
- Node version: v18.x
- commander.js version: latest

---
Repository: /testbed
