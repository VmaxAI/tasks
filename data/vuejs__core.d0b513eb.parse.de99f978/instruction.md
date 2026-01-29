# Bug Report

### Describe the bug

I'm experiencing an issue with the template parser where custom parser options are being overridden by default options instead of the other way around. When I try to pass custom options to the `parse()` function, they get ignored and the default `parserOptions` take precedence.

### Reproduction

```js
import { parse } from '@vue/compiler-dom'

const customOptions = {
  isNativeTag: (tag) => tag === 'custom-element',
  delimiters: ['[[', ']]']
}

const ast = parse('<div>[[message]]</div>', customOptions)

// Expected: Custom delimiters should be recognized
// Actual: Default delimiters {{ }} are used, custom options ignored
```

### Expected behavior

Custom parser options passed to `parse()` should override the default `parserOptions`, not the other way around. The function should respect user-provided configuration.

### System Info
- Vue version: 3.x

---
Repository: /testbed
