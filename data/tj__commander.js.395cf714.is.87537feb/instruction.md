# Bug Report

### Describe the bug

I'm experiencing an issue with command-line option matching. When I define options with both short and long forms (like `-v` and `--verbose`), the option parser doesn't recognize them correctly. It seems like the matching logic is inverted or broken somehow.

### Reproduction

```js
const program = require('commander');

program
  .option('-v, --verbose', 'enable verbose output')
  .parse(process.argv);

// Try using the short form
// node app.js -v
// Expected: option should be recognized
// Actual: option is not matched

// Try using the long form  
// node app.js --verbose
// Expected: option should be recognized
// Actual: option is not matched
```

Both the short form `-v` and long form `--verbose` fail to match, even though they're properly defined. The option parser seems to be unable to identify either form of the option.

### Expected behavior

When an option is defined with both short and long forms, either form should be correctly matched when provided on the command line. For example, both `-v` and `--verbose` should be recognized as the same option.

### System Info
- Node version: 14.x
- OS: macOS

---
Repository: /testbed
