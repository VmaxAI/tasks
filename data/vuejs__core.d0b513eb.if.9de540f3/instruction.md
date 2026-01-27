# Bug Report

### Describe the bug

I'm experiencing an issue with the `transformAssetUrl` options handling. When passing a mixed configuration object that contains both tag configurations (arrays) and other options, the function incorrectly treats it as a legacy tags-only config.

### Reproduction

```js
const options = {
  base: '/assets/',
  tags: {
    video: ['src', 'poster']
  }
}

// This gets incorrectly interpreted as legacy format
// because it checks if ANY key is an array, not ALL keys
```

The problem is that if you have a configuration object with both modern options (like `base`) and tag configs, it will be misidentified as the old format when it shouldn't be.

### Expected behavior

The function should only treat the config as legacy format when ALL keys in the options object are arrays (meaning it's purely a tags config). Mixed configurations with both tag arrays and other option properties should be handled as the modern format.

### System Info
- Vue version: 3.x

This seems like a regression in how the option format detection works. The legacy format detection is too broad and catches cases it shouldn't.

---
Repository: /testbed
