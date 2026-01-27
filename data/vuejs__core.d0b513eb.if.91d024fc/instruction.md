# Bug Report

### Describe the bug

I'm having an issue with `useSSRContext()` not working correctly in my SSR application. The function seems to always return `undefined` even though I'm calling it during server-side rendering with a properly configured SSR context.

### Reproduction

```js
import { useSSRContext } from 'vue'

// In a component during SSR
const ssrContext = useSSRContext()
console.log(ssrContext) // prints undefined instead of the context object
```

### Expected behavior

`useSSRContext()` should return the SSR context object when called during server-side rendering. The context is being provided via `inject` with the `ssrContextKey` symbol, but the function is not returning it.

### System Info
- Vue version: 3.x
- Build type: SSR (not global build)
- Node version: 18.x

This seems to have started happening recently. The SSR context is definitely being set up correctly because other parts of the application that use it directly work fine. Just `useSSRContext()` is returning undefined.

---
Repository: /testbed
