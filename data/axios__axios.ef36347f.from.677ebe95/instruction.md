# Bug Report

### Describe the bug

I'm experiencing an issue with `AxiosHeaders.from()` where it's not properly handling existing `AxiosHeaders` instances. When I pass an `AxiosHeaders` object to the `from()` method, it creates a new instance instead of returning the same instance when it should.

### Reproduction

```js
const headers1 = new AxiosHeaders({ 'Content-Type': 'application/json' });
const headers2 = AxiosHeaders.from(headers1);

// Expected: headers2 should be the same instance as headers1
// Actual: headers2 is a new instance even though headers1 is already an AxiosHeaders instance
console.log(headers1 === headers2); // Should be true, but returns false
```

### Expected behavior

When passing an `AxiosHeaders` instance to `AxiosHeaders.from()`, it should return the same instance without creating a new one (similar to how many factory methods work - if you already have the correct type, just return it).

This is causing unnecessary object creation and potential issues when comparing header instances.

### System Info
- axios version: latest
- Node.js version: 18.x

---
Repository: /testbed
