# Bug Report

### Describe the bug

I'm experiencing an issue with argument validation when using the `.choices()` method. When I specify allowed choices for an argument, the validation seems to be inverted - it's rejecting valid choices and accepting invalid ones.

### Reproduction

```js
const { program, Argument } = require('commander');

program
  .addArgument(
    new Argument('<color>', 'choose a color')
      .choices(['red', 'green', 'blue'])
  )
  .action((color) => {
    console.log(`Selected color: ${color}`);
  });

// This should work but throws an error
program.parse(['node', 'test.js', 'red']);
// Error: Allowed choices are red, green, blue.

// This should fail but is accepted
program.parse(['node', 'test.js', 'yellow']);
// Output: Selected color: yellow
```

### Expected behavior

When using `.choices()`, the program should:
- Accept values that are in the choices array ('red', 'green', 'blue')
- Reject values that are not in the choices array ('yellow', 'purple', etc.)

Currently it's doing the opposite - rejecting valid choices and accepting invalid ones.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
