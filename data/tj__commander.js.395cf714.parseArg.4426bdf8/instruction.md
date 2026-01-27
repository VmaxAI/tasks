# Bug Report

### Describe the bug

I'm experiencing an issue with argument validation when using `.choices()`. The validation logic seems to be inverted - valid choices are being rejected while invalid choices are being accepted.

### Reproduction

```js
const program = new Command();

program
  .argument('<color>', 'color choice')
  .choices(['red', 'blue', 'green'])
  .action((color) => {
    console.log(`Selected color: ${color}`);
  });

// This should work but throws an error
program.parse(['node', 'script.js', 'red']);
// Error: Allowed choices are red, blue, green.

// This should throw an error but is accepted
program.parse(['node', 'script.js', 'yellow']);
// Output: Selected color: yellow
```

### Expected behavior

When a valid choice from the allowed list is provided, it should be accepted without errors. When an invalid choice is provided, it should throw an `InvalidArgumentError` listing the allowed choices.

Currently, it's doing the opposite - rejecting valid choices and accepting invalid ones.

### Additional context

This appears to have started recently. The behavior is completely backwards from what's documented and expected.

---
Repository: /testbed
