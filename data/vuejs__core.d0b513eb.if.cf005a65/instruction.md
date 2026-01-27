# Bug Report

### Describe the bug

I'm getting unexpected warnings about invalid deprecation config keys when using the migration build with valid configuration options. The warnings appear even though I'm using documented deprecation config keys from the migration guide.

### Reproduction

```js
import { configureCompat } from 'vue'

configureCompat({
  MODE: 2,
  RENDER_FUNCTION: false,
  COMPONENT_V_MODEL: false
})
```

When running this code, I don't see any warnings about invalid config keys, but according to the migration docs these should be valid deprecation options. It seems like the validation is not working as expected - either it's not warning when it should, or it's treating valid keys as invalid.

### Expected behavior

The validation should properly identify and warn about truly invalid deprecation config keys while accepting valid ones like `RENDER_FUNCTION`, `COMPONENT_V_MODEL`, etc. that are documented in the migration build guide.

### System Info
- Vue version: 3.x (migration build)
- Node: 18.x

---
Repository: /testbed
