# Bug Report

### Describe the bug

I'm experiencing an issue with MDX parsing where constructs with `resolveAll` are being added to the `resolveAllConstructs` array even when they're already present. This appears to be causing duplicate processing of certain markdown constructs.

### Reproduction

```js
// When parsing MDX content with constructs that have resolveAll
const result = compile('# Hello\n\nSome content', {
  // ... options
})

// Constructs with resolveAll are being added multiple times
// to the resolveAllConstructs array
```

### Expected behavior

Each construct with `resolveAll` should only be added once to the `resolveAllConstructs` array. The logic should check if the construct is NOT already in the array before adding it (using `!includes` instead of `includes`).

### Additional context

This seems to be affecting the tokenizer's `addResult` function. The current behavior is adding constructs that are already in the array, when it should be adding constructs that are NOT in the array yet.

---
Repository: /testbed
