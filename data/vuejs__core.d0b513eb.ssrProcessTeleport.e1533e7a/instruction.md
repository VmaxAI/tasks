# Bug Report

### Describe the bug

When using `<Teleport>` in SSR with the `disabled` attribute set (without a value), the teleport incorrectly treats it as disabled instead of enabled. The attribute presence should enable the teleport, but it's being interpreted the opposite way.

### Reproduction

```vue
<template>
  <Teleport to="body" disabled>
    <div>Content</div>
  </Teleport>
</template>
```

When rendering this component on the server, the teleport behaves as if `disabled` is `true`, but according to HTML boolean attribute semantics, the presence of the `disabled` attribute without a value should actually mean it's disabled (which is correct), but the current behavior seems inconsistent with how the attribute is being processed.

Actually, I think I misstated the issue - when you have `disabled` as a plain attribute (no binding), it should be treated as `true` (disabled), but the current code is setting it to `true` when it should respect the attribute's presence properly.

### Expected behavior

The `disabled` attribute on Teleport should be handled correctly in SSR:
- `<Teleport disabled>` should disable the teleport
- `<Teleport :disabled="false">` should enable the teleport  
- `<Teleport :disabled="true">` should disable the teleport

The SSR output should match the client-side behavior for these cases.

### System Info
- Vue version: 3.x
- SSR environment

---
Repository: /testbed
