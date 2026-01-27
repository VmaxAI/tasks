# Bug Report

### Describe the bug

There's an issue with how form data keys are being serialized when using nested objects. The key formatting appears to be incorrect - dots and brackets are being applied in the wrong places, causing the serialized keys to have an unexpected format.

### Reproduction

```js
const formData = toFormData({
  user: {
    name: 'John',
    address: {
      city: 'NYC'
    }
  }
});

// The keys are formatted incorrectly
// Expected: user[name], user[address][city] (without dots mode)
// or: user.name, user.address.city (with dots mode)
// But getting wrong separator placement
```

### Expected behavior

When serializing nested objects to form data:
- Without dots mode: keys should be formatted as `parent[child][grandchild]`
- With dots mode: keys should be formatted as `parent.child.grandchild`

The separators (dots or brackets) should be placed correctly between all nested levels.

### System Info
- Axios version: latest
- Node version: 18.x

---
Repository: /testbed
