# Bug Report

### Describe the bug

I'm experiencing a hydration mismatch issue with inline styles. When the server-rendered HTML has different inline styles than the client-side component, Vue is not properly detecting the mismatch and showing warnings/errors as expected.

### Reproduction

```js
// Server-side renders:
<div style="color: red; font-size: 14px;"></div>

// Client-side component has:
<div style="color: blue;"></div>
```

In this case, the styles are clearly different (different number of properties and different values), but Vue seems to be treating them as equal during hydration. This causes the client-side styles to be incorrectly applied or the mismatch to go undetected.

### Expected behavior

Vue should detect that the inline styles don't match between server and client, and either:
- Show a hydration mismatch warning in development mode
- Properly update the DOM to reflect the client-side styles

Instead, it appears the style comparison is incorrectly returning that they match when they don't.

### System Info
- Vue version: 3.x
- Node: 18.x
- SSR: Yes

---
Repository: /testbed
