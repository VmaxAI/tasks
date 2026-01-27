# Bug Report

### Describe the bug

When merging configurations, the second config's values are being incorrectly applied even when they're undefined. It seems like config values from the first config are being completely ignored in certain merge scenarios.

### Reproduction

```js
const config1 = {
  timeout: 5000,
  headers: { 'X-Custom': 'value1' }
}

const config2 = {
  headers: { 'X-Other': 'value2' }
}

const merged = mergeConfig(config1, config2)

// Expected: merged.timeout should be 5000 from config1
// Actual: merged.timeout is undefined
console.log(merged.timeout) // undefined instead of 5000
```

### Expected behavior

When merging two configs, properties from the first config should be preserved if they don't exist in the second config. The `timeout` value from `config1` should carry over to the merged result.

### System Info
- axios version: latest
- Node version: 18.x

---
Repository: /testbed
