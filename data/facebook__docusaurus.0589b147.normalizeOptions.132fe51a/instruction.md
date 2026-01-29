# Bug Report

### Describe the bug

When using the swizzle command with certain flag combinations, the options are being set incorrectly. Specifically, when I use `--javascript`, it also enables TypeScript mode, and when I use `--wrap`, it also enables eject mode.

### Reproduction

```bash
# This incorrectly enables both JavaScript and TypeScript
docusaurus swizzle some-theme SomeComponent --javascript

# This incorrectly enables both wrap and eject
docusaurus swizzle some-theme SomeComponent --wrap
```

### Expected behavior

- When `--javascript` is specified, only JavaScript mode should be enabled, not TypeScript
- When `--wrap` is specified, only wrap mode should be enabled, not eject
- These flags should be mutually exclusive and not interfere with each other

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
