# Bug Report

### Describe the bug

When using the `--inspect` flag with a hostname but no port (e.g., `--inspect=localhost`), the debug configuration is not being parsed correctly. The hostname appears to be extracted from the wrong capture group in the regex match.

### Reproduction

```js
// When passing --inspect with just a hostname
const args = ['node', 'script.js', '--inspect=localhost'];

// The hostname extraction fails because it's looking at match[3] 
// instead of match[2], causing issues with the debug configuration
```

### Steps to reproduce:
1. Run a command with `--inspect=localhost` (hostname only, no port)
2. The inspector configuration gets mangled
3. Debug connection fails or uses incorrect host

### Expected behavior

The hostname should be correctly extracted from the regex match and the inspector should work properly with hostname-only specifications like `--inspect=localhost`.

### Additional context

This seems to affect the node inspector port increment logic. When you specify just a hostname without a port, it should still be handled correctly.

---
Repository: /testbed
