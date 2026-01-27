# Bug Report

### Describe the bug

When setting `NO_COLOR` environment variable to an empty string, the color output is still being disabled even though the NO_COLOR spec states that only the presence of a non-empty value should disable colors.

### Reproduction

```js
// Set NO_COLOR to empty string
process.env.NO_COLOR = '';

// Color output is incorrectly disabled
// Expected: colors should still be enabled since NO_COLOR is empty
```

According to the [NO_COLOR specification](https://no-color.org), the environment variable should only disable colors when it's set to a non-empty value. An empty string should be treated the same as the variable not being set at all.

### Expected behavior

Setting `NO_COLOR=''` (empty string) should not disable color output. Only non-empty values like `NO_COLOR=1` or `NO_COLOR=true` should disable colors.

### Additional context

This also affects `CLICOLOR_FORCE` which has similar behavior - it should only force colors when set to a non-empty value, but currently any defined value (including empty string) forces colors on.

---
Repository: /testbed
