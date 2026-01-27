# Bug Report

### Describe the bug

I'm experiencing an issue with command name matching that's causing unexpected behavior. When I define multiple commands, the wrong command gets executed because partial name matches are being accepted instead of exact matches.

### Reproduction

```js
program
  .command('deploy')
  .action(() => console.log('Running deploy'));

program
  .command('deploy-all')
  .action(() => console.log('Running deploy-all'));

// This incorrectly matches 'deploy-all' instead of 'deploy'
program.parse(['node', 'script.js', 'deploy']);
```

When I run the command `deploy`, it's matching against `deploy-all` instead because the name matching logic seems to be doing substring matching rather than exact matching.

### Expected behavior

Commands should only match by their exact name or exact alias, not by partial/substring matches. Running `deploy` should execute the `deploy` command, not `deploy-all`.

### Additional context

This seems to have started happening recently. I have several commands with similar prefixes (like `build`, `build-prod`, `build-dev`) and they're all conflicting with each other now. The command that gets executed seems unpredictable.

---
Repository: /testbed
