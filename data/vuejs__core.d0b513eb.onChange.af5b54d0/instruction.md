# Bug Report

### Describe the bug

The SSR mode checkbox in the template explorer is behaving in reverse - when I check the box, SSR mode is disabled, and when I uncheck it, SSR mode is enabled. The checkbox state is inverted from what it should be.

### Reproduction

1. Open the template explorer
2. Click the "SSR" checkbox to enable SSR mode
3. Observe that SSR mode is actually disabled instead of enabled
4. Uncheck the checkbox
5. Observe that SSR mode becomes enabled

### Expected behavior

When the SSR checkbox is checked, SSR mode should be enabled. When unchecked, SSR mode should be disabled. The checkbox state should match the actual SSR mode state.

### System Info
- Vue version: 3.x
- Template Explorer

---
Repository: /testbed
