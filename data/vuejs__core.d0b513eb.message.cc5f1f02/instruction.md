# Bug Report

### Describe the bug

The deprecation warning message for `ATTR_FALSE_VALUE` contains incorrect information. When using `v-bind` with a `false` value, the warning states that the attribute will render as `"true"` instead of the correct behavior (`"false"`), and it also suggests using the wrong configuration value in the `configureCompat` call.

### Reproduction

```js
// In a Vue 3 migration compat mode setup
<template>
  <div v-bind:data-enabled="false"></div>
</template>
```

When this code runs in compat mode, the deprecation warning displays:
```
Attribute "data-enabled" with v-bind value `false` will render data-enabled="true" instead of removing it in Vue 3...
```

But the actual behavior is that it renders `data-enabled="false"`.

Additionally, the warning suggests:
```
configureCompat({ ATTR_FALSE_VALUE: true })
```

Which seems incorrect based on the context.

### Expected behavior

The deprecation warning should accurately describe what happens when binding `false` to an attribute:
- It should say the attribute will render as `"false"` (not `"true"`)
- The configuration example should use the appropriate boolean value

### System Info
- Vue version: 3.x (compat mode)

---
Repository: /testbed
