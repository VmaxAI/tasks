# Bug Report

### Describe the bug

When using the Options API in SFC (Single File Components), the first property defined in component options appears to be ignored during compilation. This affects properties like `data`, `props`, `computed`, `methods`, etc. when they are the first property in the options object.

### Reproduction

```vue
<script>
export default {
  props: ['message'],
  data() {
    return {
      count: 0
    }
  },
  methods: {
    increment() {
      this.count++
    }
  }
}
</script>
```

In the above example, `props` is not being recognized properly. If you move `props` to a different position (not first), it works as expected:

```vue
<script>
export default {
  data() {
    return {
      count: 0
    }
  },
  props: ['message'],  // Works when not first
  methods: {
    increment() {
      this.count++
    }
  }
}
</script>
```

### Expected behavior

All properties in the component options object should be processed correctly regardless of their position. The first property should not be skipped during script analysis.

### System Info
- Vue version: 3.x
- Using SFC compiler

---
Repository: /testbed
