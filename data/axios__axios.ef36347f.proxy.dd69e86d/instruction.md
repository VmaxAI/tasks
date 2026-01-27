# Bug Report

### Describe the bug

I'm experiencing an issue with proxy configuration when following redirects. After a redirect occurs, the proxy settings aren't being applied correctly to the redirected request. It seems like the wrong parameters are being passed when reconfiguring the proxy for the redirect.

### Reproduction

```js
const axios = require('axios');

const instance = axios.create({
  proxy: {
    host: 'proxy.example.com',
    port: 8080,
    protocol: 'http'
  }
});

// Make a request that results in a redirect
instance.get('http://example.com/redirect-me')
  .then(response => {
    console.log('Success');
  })
  .catch(error => {
    console.error('Proxy configuration lost after redirect');
  });
```

### Expected behavior

The proxy configuration should be maintained and correctly applied to the redirected request, using the same proxy settings as the original request.

### System Info
- axios version: latest
- Node.js version: 18.x
- OS: Linux

---
Repository: /testbed
