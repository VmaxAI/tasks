# Bug Report

### Describe the bug

I'm encountering an issue with directive modifiers in templates. When using a directive with a modifier (e.g., `v-on.stop` or `v-model.trim`), the modifier portion seems to be getting cut off or not parsed correctly.

### Reproduction

```vue
<template>
  <input v-model.trim="text" />
  <button v-on.stop="handleClick">Click me</button>
</template>
```

When the template is compiled, the directive modifiers don't seem to be recognized properly. The directives work but the modifiers appear to be ignored or incorrectly processed.

### Expected behavior

Directive modifiers should be parsed and applied correctly. For example:
- `v-model.trim` should trim whitespace from input values
- `v-on.stop` should call `stopPropagation()` on the event

### System Info
- Vue version: 3.x
- Template compiler: latest

---
Repository: /testbed
