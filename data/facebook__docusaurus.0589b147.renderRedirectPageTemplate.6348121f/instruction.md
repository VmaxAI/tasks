# Bug Report

### Describe the bug

Redirect pages are not working correctly after a recent change. The redirect metadata and functionality seem to be broken - the page doesn't include the proper delay or search/anchor forwarding configuration.

### Reproduction

Create a redirect configuration with custom delay and search/anchor forwarding:

```js
{
  redirects: [
    {
      from: '/old-page',
      to: '/new-page',
    }
  ],
  createRedirects(existingPath) {
    // ...
  }
}
```

When navigating to the old URL, the redirect page is generated but it doesn't respect the delay setting or properly forward search parameters and anchors from the original URL.

### Expected behavior

The redirect page should:
1. Include the configured delay before redirecting
2. Forward search parameters (e.g., `?foo=bar`)
3. Forward URL anchors (e.g., `#section`)

All of this configuration data should be passed to the redirect page template so it can function properly.

### System Info
- Docusaurus version: latest
- Plugin: @docusaurus/plugin-client-redirects

---
Repository: /testbed
