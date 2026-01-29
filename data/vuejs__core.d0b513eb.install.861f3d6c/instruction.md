# Bug Report

### Describe the bug

When using a plugin without options that checks `this._installed` in its install method, the plugin fails to install properly. The `this` context doesn't have the expected `_installed` property, causing the plugin to not register correctly.

### Reproduction

```js
const PluginNoOptions = {
  install(app) {
    if (this._installed) {
      return;
    }
    
    this._installed = true;
    
    app.config.globalProperties.$plugin = this;
  }
}

app.use(PluginNoOptions)
// Plugin doesn't install as expected
```

### Expected behavior

The plugin should install successfully and `app.config.globalProperties.$plugin` should be set. The `this._installed` check should work correctly to prevent duplicate installations.

### System Info
- Vue version: 3.x

---
Repository: /testbed
