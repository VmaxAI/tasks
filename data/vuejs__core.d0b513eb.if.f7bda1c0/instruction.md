# Bug Report

### Describe the bug

I'm getting an incorrect warning message when using the compiler in browser builds. The warning says `decodeEntities option is passed but will be ignored in non-browser builds` even though I'm running in a browser environment.

### Reproduction

```js
import { baseParse } from '@vue/compiler-core'

// In browser environment
const ast = baseParse('<div>Hello &amp; World</div>', {
  decodeEntities: (text) => text.replace(/&amp;/g, '&')
})

// Console shows: "[@vue/compiler-core] decodeEntities option is passed but will be ignored in non-browser builds."
// But this is actually running in a browser!
```

### Expected behavior

When running in a browser with `decodeEntities` provided, no warning should be shown. The warning about ignoring the option should only appear in non-browser builds.

### System Info
- Vue version: 3.x
- Environment: Browser (Chrome/Firefox)

---
Repository: /testbed
