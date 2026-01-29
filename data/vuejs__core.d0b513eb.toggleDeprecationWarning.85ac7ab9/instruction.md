# Bug Report

### Describe the bug

The `toggleDeprecationWarning()` function is not working as expected. When trying to disable deprecation warnings by calling `toggleDeprecationWarning(false)`, the warnings are still being shown. It seems like the function doesn't properly toggle the warning state anymore.

### Reproduction

```js
import { toggleDeprecationWarning } from '@vue/compat'

// Try to disable warnings
toggleDeprecationWarning(false)

// Use deprecated feature - warning still appears
// Expected: no warning should be shown
```

### Expected behavior

When calling `toggleDeprecationWarning(false)`, all deprecation warnings should be suppressed. When calling `toggleDeprecationWarning(true)`, warnings should be enabled again.

Currently it seems like once warnings are enabled, they can't be disabled, or the toggle behavior is inverted/broken.

### System Info
- Vue version: 3.x
- Using @vue/compat for migration

---
Repository: /testbed
