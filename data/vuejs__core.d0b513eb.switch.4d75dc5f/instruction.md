# Bug Report

### Describe the bug

I'm experiencing an issue where component properties are being accessed from the wrong source. When I have both `data()` and `setup()` returning properties with the same name, the values returned are swapped - accessing a setup property returns the data value and vice versa.

### Reproduction

```js
export default {
  data() {
    return {
      message: 'from data'
    }
  },
  setup() {
    return {
      message: 'from setup'
    }
  },
  mounted() {
    console.log(this.message) // Expected: 'from setup', Actual: 'from data'
  }
}
```

Another example with different property names:

```js
export default {
  data() {
    return {
      count: 100
    }
  },
  setup() {
    return {
      value: 42
    }
  },
  mounted() {
    console.log(this.count) // Expected: 100, Actual: undefined or wrong value
    console.log(this.value) // Expected: 42, Actual: undefined or wrong value
  }
}
```

### Expected behavior

Properties should be resolved correctly according to Vue's priority rules. Setup properties should take precedence over data properties when both exist, and each should return their correct values.

### System Info
- Vue version: 3.x
- Node: 18.x

---
Repository: /testbed
