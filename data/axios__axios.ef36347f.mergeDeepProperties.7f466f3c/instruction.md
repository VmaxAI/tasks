# Bug Report

### Describe the bug

When merging configurations, the second config's properties are not properly overriding the first config's properties. It seems like the merge order is reversed - instead of config2 taking precedence over config1, config1 values are being used even when config2 has values defined.

### Reproduction

```js
const config1 = {
  headers: {
    'Content-Type': 'application/json'
  },
  timeout: 5000
}

const config2 = {
  headers: {
    'Content-Type': 'text/plain'
  },
  timeout: 10000
}

const merged = mergeConfig(config1, config2)

// Expected: merged.timeout should be 10000 (from config2)
// Actual: merged.timeout is 5000 (from config1)
console.log(merged.timeout) // prints 5000 instead of 10000
```

### Expected behavior

When merging two configs, the second config should override values from the first config. If both config1 and config2 have the same property defined, the value from config2 should be used in the merged result.

### System Info
- axios version: latest
- Node version: 18.x

---
Repository: /testbed
