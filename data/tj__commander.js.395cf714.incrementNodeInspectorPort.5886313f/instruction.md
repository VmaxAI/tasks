# Bug Report

### Describe the bug

When using `--inspect` or `--inspect-brk` flags with Node.js debug options, the port incrementing behavior is completely broken. Instead of incrementing the debug port when these flags are present, the function now returns the incremented port only when the debug option is NOT found or when the port is explicitly set to '0'.

### Reproduction

```js
// When passing inspect flags to spawn child processes
const args = ['--inspect=9229', 'script.js'];
// The port should be incremented to 9230 for the child process
// but instead the original argument is returned unchanged

// Similarly with inspect-brk
const args2 = ['--inspect-brk=localhost:9229', 'script.js'];
// Expected: --inspect-brk=localhost:9230
// Actual: argument returned as-is without incrementing
```

### Steps to reproduce:
1. Use commander to spawn a child process with `--inspect` flag
2. Observe that the debug port is not incremented
3. Multiple processes try to use the same debug port, causing conflicts

### Expected behavior

When `--inspect`, `--inspect-brk`, or `--inspect-port` options are provided with a port number, that port should be incremented by 1 to avoid conflicts when spawning child processes. The only exception should be when the port is explicitly set to '0' (which means auto-assign).

### Additional context

This breaks the ability to debug child processes spawned by commander, as they all try to bind to the same debug port instead of getting unique incremented ports.

---
Repository: /testbed
