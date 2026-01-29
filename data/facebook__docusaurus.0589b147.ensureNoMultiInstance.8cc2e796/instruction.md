# Bug Report

### Describe the bug

I'm getting an error when trying to use the Vercel Analytics plugin with the default configuration. The plugin throws an error saying it's using a custom plugin id, even though I haven't specified any custom id at all.

### Reproduction

```js
// docusaurus.config.js
module.exports = {
  plugins: [
    '@docusaurus/plugin-vercel-analytics',
  ],
};
```

When I start the site, I get this error:

```
Error: You site uses the Vercel Analytics plugin with a custom plugin id (name=default).
But this plugin is only supposed to be used at most once per site. Therefore providing a custom plugin id is unsupported.
```

### Expected behavior

The plugin should work fine with the default configuration without any custom id. The error should only appear when I actually provide a custom plugin id, not when using the default one.

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
