# Bug Report

### Describe the bug

When using the swizzle command with the `--wrap` flag, the component is not being wrapped as expected. Instead, it seems like the wrap option is being ignored and the behavior is inverted.

### Reproduction

```bash
docusaurus swizzle @docusaurus/theme-classic Footer --wrap
```

Expected: The Footer component should be wrapped
Actual: The component is not wrapped (behaves as if `--wrap` was not specified)

### Steps to reproduce

1. Run the swizzle command with `--wrap` flag on any theme component
2. Check the generated component file
3. The component is not wrapped despite the flag being present

This seems to have started happening recently. The `--wrap` option used to work correctly before.

### Expected behavior

When the `--wrap` flag is provided, the swizzle command should wrap the component rather than ejecting it directly.

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
