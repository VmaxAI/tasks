# Bug Report

### Describe the bug

The command-line argument formatting is displaying incorrectly in the help output. Required arguments are being shown in square brackets `[arg]` instead of angle brackets `<arg>`, and optional arguments are being shown in angle brackets `<arg>` instead of square brackets `[arg]`. This is backwards from the standard convention.

Additionally, the variadic indicator `...` is being added to arguments that shouldn't have it.

### Reproduction

```js
const { Argument } = require('./lib/argument');

// Required argument
const requiredArg = new Argument('file', 'input file');
requiredArg.required = true;
console.log(requiredArg.humanReadableArgName());
// Currently outputs: [file]
// Should output: <file>

// Optional argument
const optionalArg = new Argument('output', 'output file');
optionalArg.required = false;
console.log(optionalArg.humanReadableArgName());
// Currently outputs: <output>
// Should output: [output]

// Variadic argument
const variadicArg = new Argument('files', 'input files');
variadicArg.variadic = false;
console.log(variadicArg.humanReadableArgName());
// Currently outputs: files...
// Should output: files
```

### Expected behavior

- Required arguments should be displayed as `<arg>`
- Optional arguments should be displayed as `[arg]`
- The `...` suffix should only appear when `variadic === true`, not when it's `false` or any other value

This is causing confusion in the help text as users can't tell which arguments are required vs optional.

---
Repository: /testbed
