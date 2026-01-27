# Bug Report

### Describe the bug

I'm getting a confusing warning message when using the compiler in a browser environment. The warning says `decodeEntities option is passed but will be ignored in non-browser builds`, but I'm actually running this in a browser, not in a Node.js environment.

### Reproduction

```js
import { compile } from '@vue/compiler-dom'

// Running this in a browser
const result = compile('<div>&amp;</div>', {
  decodeEntities: (rawText) => rawText.replace(/&amp;/g, '&')
})

// Console shows:
// "[@vue/compiler-core] decodeEntities option is passed but will be ignored in non-browser builds."
```

### Expected behavior

When running in a browser with `decodeEntities` option provided, I should either:
1. Not see any warning (since this is a browser build), OR
2. See an error if the option is required but not provided correctly

The current warning message doesn't make sense for browser environments.

### System Info
- Vue version: 3.x
- Environment: Browser (Chrome 120)

---
Repository: /testbed
