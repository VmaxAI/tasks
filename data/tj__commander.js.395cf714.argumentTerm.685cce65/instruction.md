# Bug Report

### Describe the bug

I'm experiencing an issue with the help formatter where argument terms are not being displayed correctly. Instead of showing the argument name as a string, it appears to be showing the entire argument object.

### Reproduction

```js
const program = new Command();
program
  .argument('<file>', 'file to process')
  .configureHelp({
    formatHelp: (cmd, helper) => {
      return helper.argumentTerm(cmd.registeredArguments[0]);
    }
  });

console.log(program.helpInformation());
// Expected: "file"
// Actual: [object Object] or similar
```

### Expected behavior

The `argumentTerm()` method should return the argument name as a string (e.g., "file"), not the argument object itself. This is breaking custom help formatters that rely on getting the string representation of arguments.

### System Info
- commander.js version: latest
- Node version: 18.x

---
Repository: /testbed
