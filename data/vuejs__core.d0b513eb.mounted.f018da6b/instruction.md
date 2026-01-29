# Bug Report

### Describe the bug

I'm encountering an issue with type inference when using `mixins` in `defineComponent`. The type of properties from mixins seems to be incorrect in lifecycle hooks.

### Reproduction

```ts
const CompWithC = defineComponent({
  data() {
    return {
      foo: 123
    }
  }
})

const CompEmpty = defineComponent({})

defineComponent({
  mixins: [CompWithC, CompEmpty],
  created() {
    // Expected: this.foo should be typed as number
    // Actual: this.foo is typed as string
    console.log(this.foo)
  }
})
```

### Expected behavior

When using mixins, the properties from the mixed-in component should maintain their original types in lifecycle hooks. In this case, `this.foo` should be typed as `number` since that's what `CompWithC` defines in its `data()` function.

### System Info
- Vue version: 3.x
- TypeScript version: latest

---
Repository: /testbed
