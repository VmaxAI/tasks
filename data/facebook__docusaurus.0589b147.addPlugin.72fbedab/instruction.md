# Bug Report

### Describe the bug

I'm experiencing an issue with plugin registration in the unified processor. When attempting to use the `.use()` method with plugins, it seems like the plugin lookup is failing and plugins aren't being found correctly when they should already be registered.

### Reproduction

```js
const processor = unified()
  .use(somePlugin, { option1: 'value1' })
  .use(somePlugin, { option2: 'value2' }) // Should merge options with existing plugin

// The second .use() call doesn't seem to find the existing plugin entry
// and creates a duplicate instead of merging the options
```

### Expected behavior

When calling `.use()` with the same plugin multiple times, the processor should:
1. Detect that the plugin is already registered
2. Merge the new options with the existing ones (for plain objects)
3. Not create duplicate plugin entries

Instead, it appears the plugin lookup is broken and always treats plugins as new entries.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
