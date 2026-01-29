# Bug Report

### Describe the bug

Props destructuring is not working when the `propsDestructure` compiler option is explicitly set to `'error'` or `'all'`. The feature seems to be completely disabled even when it should be enabled.

### Reproduction

```vue
<script setup lang="ts">
const { foo, bar } = defineProps<{
  foo: string
  bar: number
}>()
</script>
```

With compiler options:
```js
{
  propsDestructure: 'error' // or 'all'
}
```

### Expected behavior

Props destructuring should work when `propsDestructure` is set to `'error'` or `'all'`. The transformation should only be disabled when the option is explicitly set to `false` or left undefined.

According to the documentation, the `propsDestructure` option can be:
- `false` - disable the feature
- `'error'` - enable with error on access outside of setup
- `'all'` - enable for all cases

Currently, it seems like only `false` is being handled correctly, but the other valid values are being treated the same as `false`.

### System Info
- Vue version: 3.4.x
- Compiler: @vue/compiler-sfc

---
Repository: /testbed
