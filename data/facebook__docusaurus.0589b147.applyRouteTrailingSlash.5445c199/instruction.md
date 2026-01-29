# Bug Report

### Describe the bug

When configuring routes with nested subroutes, the trailing slash configuration is not being applied recursively to deeply nested route paths. Only the top-level route and its immediate children get the trailing slash applied correctly, but any deeper nested routes remain unchanged.

### Reproduction

```js
const route = {
  path: '/docs',
  routes: [
    {
      path: '/docs/intro',
      routes: [
        {
          path: '/docs/intro/getting-started'
        }
      ]
    }
  ]
}

// After applying trailing slash with trailingSlash: true
// Expected: all paths should have trailing slashes
// Actual: only /docs/ and /docs/intro/ get trailing slashes
// /docs/intro/getting-started remains without trailing slash
```

### Expected behavior

All nested route paths at every level should have the trailing slash configuration applied consistently, not just the first two levels.

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
