# Bug Report

### Describe the bug

When using the `--inspect` or `--inspect-brk` flags without specifying a port number, the debugger doesn't start properly. It seems like the port configuration is not being handled correctly when only the flag is provided without an explicit port value.

### Reproduction

```bash
node --inspect myapp.js
```

or

```bash
node --inspect-brk myapp.js
```

When running commands with these flags (without specifying a port), the debugger fails to initialize with the default port 9229 as expected.

### Expected behavior

The debugger should start on the default port (9229) when `--inspect` or `--inspect-brk` is used without an explicit port number. This is the standard Node.js behavior and should be preserved when these arguments are processed.

### System Info
- Node.js version: 18.x
- OS: Linux

---
Repository: /testbed
