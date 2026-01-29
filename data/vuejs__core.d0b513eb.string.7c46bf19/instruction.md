# Bug Report

### Describe the bug

When hydrating components with inline styles that contain colons in their values (like `url()` or time values), the style attributes are not being hydrated correctly. The styles appear to be lost or not applied during hydration.

### Reproduction

```js
// Server-rendered HTML with inline style containing colons
<div style="background-image: url(data:image/svg+xml;base64,...); width: 100px"></div>

// After hydration, the styles are missing or incomplete
```

Another example:
```js
<div style="transition: all 0.3s ease; transform: rotate(45deg)"></div>
// Styles don't hydrate properly
```

### Expected behavior

Inline styles with values containing colons (like `url(data:...)`, time values, etc.) should be preserved and correctly hydrated. The component should maintain all its styles after hydration without any loss.

### System Info
- Vue version: 3.x
- Environment: SSR with hydration

---
Repository: /testbed
