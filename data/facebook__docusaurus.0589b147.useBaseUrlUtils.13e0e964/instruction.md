# Bug Report

### Describe the bug

The `useBaseUrl` hook is generating incorrect URLs. When I try to use it with a path, the resulting URL has the arguments mixed up - it looks like `siteUrl` and `baseUrl` are being passed in the wrong order to the internal `addBaseUrl` function.

### Reproduction

```js
import { useBaseUrl } from '@docusaurus/useBaseUrl';

function MyComponent() {
  const baseUrl = useBaseUrl('/docs/intro');
  
  // Expected: correct URL with base path applied
  // Actual: malformed URL with siteUrl and baseUrl swapped
  console.log(baseUrl);
}
```

### Expected behavior

The hook should correctly combine the site URL, base URL, and provided path to generate a valid URL. The parameters should be passed to `addBaseUrl` in the correct order so that URLs are constructed properly.

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
