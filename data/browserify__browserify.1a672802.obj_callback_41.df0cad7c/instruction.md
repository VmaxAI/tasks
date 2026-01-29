# Bug Report

### Describe the bug

The `--deps` flag output is broken - it's not producing any output to stdout anymore. When I run browserify with `--deps`, I just get an empty result instead of the dependency tree.

### Reproduction

```bash
browserify main.js --deps
```

Expected: JSON stream of dependencies
Actual: No output

This was working fine before, but now when I try to pipe the deps output or just view it in the console, nothing shows up. The build itself still works if I remove the `--deps` flag, so it's specifically an issue with the dependency output.

### Steps to reproduce

1. Create a simple entry file with some requires
2. Run `browserify entry.js --deps`
3. Notice that no dependency information is written to stdout

### Expected behavior

Should output a JSON stream with dependency information for each module, like it used to.

---
Repository: /testbed
