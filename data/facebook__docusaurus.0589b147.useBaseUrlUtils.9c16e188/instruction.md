# Bug Report

### Describe the bug

The `useBaseUrl` hook is generating incorrect URLs when both `siteUrl` and `baseUrl` are configured. The resulting URLs appear to have the parameters reversed, causing links and assets to point to wrong locations.

### Reproduction

```js
// In docusaurus.config.js
module.exports = {
  url: 'https://example.com',
  baseUrl: '/docs/',
  // ... other config
}

// In a component
import useBaseUrl from '@docusaurus/useBaseUrl';

function MyComponent() {
  const {withBaseUrl} = useBaseUrlUtils();
  const url = withBaseUrl('/getting-started');
  
  console.log(url);
  // Expected: https://example.com/docs/getting-started
  // Actual: incorrect URL structure
}
```

### Expected behavior

When calling `withBaseUrl()`, it should correctly combine the site URL and base URL with the provided path to generate proper absolute URLs.

### System Info

- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
