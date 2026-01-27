# Bug Report

### Describe the bug

The argument names in help text are displaying with incorrect bracket notation. Required arguments are showing up in square brackets `[]` instead of angle brackets `<>`, and optional arguments are showing in angle brackets instead of square brackets. Additionally, variadic arguments (those that accept multiple values) are not getting the `...` suffix appended correctly.

### Reproduction

```js
const { Argument } = require('./lib/argument');

// Required argument
const requiredArg = new Argument('file', 'input file');
console.log(requiredArg.argName());
// Currently shows: [file]
// Expected: <file>

// Optional argument  
const optionalArg = new Argument('[output]', 'output file');
console.log(optionalArg.argName());
// Currently shows: <output>
// Expected: [output]

// Variadic argument
const variadicArg = new Argument('<files...>', 'input files');
console.log(variadicArg.argName());
// Currently shows: <files>
// Expected: <files...>
```

### Expected behavior

- Required arguments should be wrapped in angle brackets: `<argument>`
- Optional arguments should be wrapped in square brackets: `[argument]`  
- Variadic arguments should have `...` appended: `<files...>` or `[files...]`

This is causing confusion in the help output since the convention is backwards from what users expect.

---
Repository: /testbed
