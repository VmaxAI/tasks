# Bug Report

### Describe the bug

When using `Vue.use()` with plugin objects in compat mode, plugins that have both a callable function signature AND an `install` method are not being handled correctly. The plugin system seems to be checking conditions in the wrong order, causing plugins with an `install` method to be called as functions instead.

### Reproduction

```js
const myPlugin = function(Vue, options) {
  // This gets called instead of install method
  console.log('Function called')
}

myPlugin.install = function(Vue, options) {
  // This should be called but isn't
  console.log('Install method called')
  Vue.mixin({ ... })
}

Vue.use(myPlugin, { someOption: true })
```

### Expected behavior

When a plugin has an `install` method, `Vue.use()` should prioritize calling `plugin.install()` over treating the plugin as a plain function. The `install` method should be invoked, not the function itself.

This is how Vue 2 behaves and is documented in the official plugin API.

### System Info
- Vue version: 3.x (compat mode)
- Running in compatibility layer with Vue 2.6.14-compat

---
Repository: /testbed
