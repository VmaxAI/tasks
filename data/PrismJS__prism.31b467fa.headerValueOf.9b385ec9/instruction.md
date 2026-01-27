# Bug Report

### Describe the bug

I'm experiencing an issue with HTTP header parsing where headers with values are not being recognized correctly. It seems like headers that have actual content after the colon are being ignored or not matched properly.

### Reproduction

```http
Content-Type: application/json
Authorization: Bearer token123
```

When parsing HTTP headers like the above, the header values are not being captured. The regex pattern seems to require whitespace immediately after the colon and header name, which prevents it from matching headers that have actual values.

### Expected behavior

HTTP headers with values should be parsed correctly. For example:
- `Content-Type: application/json` should match and capture `application/json`
- `Authorization: Bearer token123` should match and capture `Bearer token123`

The current behavior seems to only match headers that have whitespace after the colon but no actual content, which is the opposite of what we need.

### System Info
- Latest version from main branch

---
Repository: /testbed
