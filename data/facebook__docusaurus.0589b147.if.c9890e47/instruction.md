# Bug Report

### Describe the bug

I'm experiencing an issue with sidebar configuration in the docs plugin. When I set `sidebarCollapsible: false` without explicitly setting `sidebarCollapsed`, the sidebar items are appearing as expanded instead of collapsed. This seems backwards from what I would expect.

### Reproduction

```js
// docusaurus.config.js
module.exports = {
  presets: [
    [
      '@docusaurus/preset-classic',
      {
        docs: {
          sidebarCollapsible: false,
          // sidebarCollapsed is not set
        },
      },
    ],
  ],
};
```

When I load the docs, all sidebar items are expanded by default. I expected them to be collapsed since `sidebarCollapsible` is set to false.

### Expected behavior

When `sidebarCollapsible: false` is set and `sidebarCollapsed` is undefined, the sidebar items should default to a collapsed state (or at least behave consistently).

### System Info

- Docusaurus version: latest
- Node version: 18.x
- OS: macOS

This might be related to how the default values are being set for these options. The behavior seems inconsistent with the option names.

---
Repository: /testbed
