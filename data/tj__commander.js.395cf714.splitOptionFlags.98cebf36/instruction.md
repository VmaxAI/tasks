# Bug Report

### Describe the bug

I'm encountering an issue with parsing option flags when using two long flags (e.g., `--ws, --workspace`). The parser doesn't seem to be handling the case correctly where you want to define two long-form flags without a short flag.

### Reproduction

```js
// Trying to define an option with two long flags
program.option('--ws, --workspace <path>', 'Set workspace path')

// The flags are not being parsed correctly
// Expected: both --ws and --workspace should work as the long flag
// Actual: the behavior is inconsistent
```

When I try to use `--ws` or `--workspace`, the option doesn't get recognized properly. It seems like the flag parsing logic isn't correctly identifying when we have two long flags without a short flag prefix.

### Expected behavior

Both `--ws` and `--workspace` should be recognized as valid long flags for the same option, with `--ws` being treated as the "short" long flag and `--workspace` as the primary long flag.

### System Info
- Node version: 18.x
- OS: macOS

---
Repository: /testbed
