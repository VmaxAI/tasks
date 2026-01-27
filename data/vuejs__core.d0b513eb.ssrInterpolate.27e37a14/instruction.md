# Bug Report

### Describe the bug

I'm experiencing an issue with server-side rendering where HTML entities in interpolated string values are not being properly escaped. When rendering strings that contain special characters like `<`, `>`, `&`, etc., they appear as-is in the HTML output instead of being converted to their entity equivalents (`&lt;`, `&gt;`, `&amp;`).

This is a security concern as it could potentially lead to XSS vulnerabilities if user-generated content contains malicious HTML.

### Reproduction

```js
// Server-side rendering
const app = createSSRApp({
  template: `<div>{{ message }}</div>`,
  data() {
    return {
      message: '<script>alert("xss")</script>'
    }
  }
})

const html = await renderToString(app)
console.log(html)
// Output: <div><script>alert("xss")</script></div>
// Expected: <div>&lt;script&gt;alert("xss")&lt;/script&gt;</div>
```

The string interpolation in SSR is not escaping HTML characters, which means any HTML tags or entities in the data are rendered directly into the markup.

### Expected behavior

String values should be HTML-escaped during SSR interpolation to prevent injection attacks. Special characters should be converted to their HTML entity equivalents:
- `<` → `&lt;`
- `>` → `&gt;`
- `&` → `&amp;`
- `"` → `&quot;`
- `'` → `&#39;`

### System Info
- Vue version: 3.x
- Node version: 18.x
- SSR environment

---
Repository: /testbed
