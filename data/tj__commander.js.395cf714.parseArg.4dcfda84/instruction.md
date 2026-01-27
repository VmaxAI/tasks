# Bug Report

### Describe the bug

I'm experiencing an issue with argument validation when using `.choices()` on command arguments. When I specify allowed choices for an argument, the validation is behaving in the opposite way - it's rejecting valid choices and accepting invalid ones.

### Reproduction

```js
const program = new Command();

program
  .argument('<type>', 'deployment type')
  .choices(['production', 'staging', 'development'])
  .action((type) => {
    console.log(`Deploying to: ${type}`);
  });

program.parse(['node', 'script.js', 'production']);
```

### Expected behavior

The command should accept `'production'` since it's in the allowed choices list. Instead, it throws an error saying "Allowed choices are production, staging, development."

If I try passing an invalid choice like `'invalid'`, it actually gets accepted when it should be rejected.

### Additional context

This seems to affect both regular and variadic arguments with choices. The validation logic appears to be inverted somehow.

---
Repository: /testbed
