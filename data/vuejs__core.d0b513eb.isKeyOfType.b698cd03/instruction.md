# Bug Report

### Describe the bug

I'm experiencing an issue with component options inheritance when using mixins. It seems like the behavior has changed and now all mixins need to have a specific property for it to be recognized, rather than just one of them having it.

### Reproduction

```js
const MixinA = {
  props: {
    foo: String
  }
}

const MixinB = {
  props: {
    bar: String
  }
}

const Component = {
  mixins: [MixinA, MixinB],
  props: {
    baz: String
  }
}

// Expected: 'foo' should be recognized as a valid prop
// Actual: 'foo' is not being detected correctly
```

When a component uses multiple mixins that define different props (or computed properties, methods, etc.), the properties from the mixins aren't being recognized properly. It seems like the check is now requiring ALL mixins to have the property instead of ANY mixin having it.

### Expected behavior

If any mixin in the mixins array defines a property, that property should be recognized as part of the component's options. The current behavior seems to require all mixins to define the same property, which doesn't make sense for the mixin pattern.

### System Info
- Vue version: 3.x
- Environment: Development with custom formatter enabled

---
Repository: /testbed
