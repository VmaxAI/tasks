# Bug Report

### Describe the bug

The swizzle command is not respecting the `--typescript` flag correctly. When I explicitly pass `--typescript=false` to disable TypeScript, it actually enables it instead. The behavior is completely inverted from what I expect.

### Reproduction

```bash
# Try to disable TypeScript explicitly
docusaurus swizzle some-theme SomeComponent --typescript=false

# Result: TypeScript is enabled (creates .tsx file instead of .jsx)
# Expected: TypeScript should be disabled (should create .jsx file)
```

Also noticed that when using both `--wrap` and `--eject` flags together, the behavior seems off - it looks like they're mutually exclusive now but both flags get set to false instead of respecting the one that was passed.

```bash
# Try to wrap a component
docusaurus swizzle some-theme SomeComponent --wrap

# If eject was somehow set, wrap gets disabled
```

### Expected behavior

- When `--typescript=false` is passed, TypeScript should be disabled
- When `--typescript=true` or `--typescript` is passed, TypeScript should be enabled  
- The `--wrap` and `--eject` flags should work independently unless there's a specific reason they conflict

### System Info

- Docusaurus version: latest
- Node version: 18.x
- OS: macOS

---
Repository: /testbed
