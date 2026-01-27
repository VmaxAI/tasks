# Bug Report

### Describe the bug

When using `app.use()` to register plugins, the same plugin can now be installed multiple times, and the warning message appears in the wrong scenario. The warning "Plugin has already been applied to target app." is now shown when a plugin is being installed for the first time, instead of when attempting to install it a second time.

### Reproduction

```js
import { createApp } from 'vue'

const app = createApp({})

const myPlugin = {
  install(app) {
    console.log('Plugin installed')
  }
}

// First installation - incorrectly shows warning
app.use(myPlugin)

// Second installation - should show warning but doesn't
app.use(myPlugin)
```

### Expected behavior

- First call to `app.use(myPlugin)` should install the plugin without any warning
- Second call to `app.use(myPlugin)` should show the warning "Plugin has already been applied to target app." and skip installation
- The plugin's install method should only be called once

### Actual behavior

- First installation shows the warning (incorrect)
- Plugin can be installed multiple times without proper prevention
- The install method gets called multiple times

This seems like a regression as the plugin deduplication was working correctly before.

---
Repository: /testbed
