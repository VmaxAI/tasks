# Bug Report

### Describe the bug

When setting `prev` or `next` navigation links in doc front matter with an empty string value, the navigation link is being returned as `null` instead of `undefined`. This causes inconsistent behavior in the navigation component rendering.

### Reproduction

In a doc's front matter:
```yaml
---
id: my-doc
pagination_prev: ''
pagination_next: some-other-doc
---
```

The `pagination_prev` with empty string should be treated the same as if it wasn't specified at all, but instead it's returning a different value type which breaks the expected navigation behavior.

### Expected behavior

Empty string values for `pagination_prev` and `pagination_next` should be handled the same way as `null` or `undefined` values - by returning `undefined` to indicate no navigation link should be displayed.

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
