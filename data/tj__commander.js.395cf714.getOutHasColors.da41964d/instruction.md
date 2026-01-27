# Bug Report

### Describe the bug

When using the library with output redirection (e.g., piping to a file or another command), colored output is being written to stdout even when colors should be disabled. This results in ANSI color codes appearing in the output when it shouldn't.

### Reproduction

```bash
# This should produce plain text output but includes color codes
node myapp.js > output.txt

# Or when piping
node myapp.js | less
```

The output file contains ANSI escape sequences like `\x1b[32m` even though stdout is not a TTY.

### Expected behavior

When stdout is redirected (not a TTY), the output should be plain text without any color codes, similar to how most CLI tools behave. Colors should only be enabled when:
1. Explicitly enabled via environment variables/flags, OR
2. Writing to a TTY that supports colors

### System Info
- Node version: 18.x
- OS: Linux

This seems to be checking the wrong stream for TTY detection when determining if colors should be used for stdout.

---
Repository: /testbed
