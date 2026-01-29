# Bug Report

### Describe the bug

After a recent update, browserify is throwing errors when trying to load plugins. The plugin loading mechanism seems to be broken - I'm getting "cannot find plugin" errors even though the plugins are installed and were working before.

### Reproduction

```js
// Using browserify CLI with a plugin
browserify index.js -p some-plugin -o bundle.js
```

Or programmatically:

```js
const browserify = require('browserify');
const b = browserify();
b.plugin('my-plugin', { options: 'here' });
```

### Expected behavior

The plugin should load successfully without errors. This was working fine in previous versions.

### Additional context

The error message says something like "cannot find plugin" or "plugin does not export a function", but the plugin is definitely installed in node_modules and hasn't changed. It seems like the plugin resolution or loading logic might have an issue.

---
Repository: /testbed
