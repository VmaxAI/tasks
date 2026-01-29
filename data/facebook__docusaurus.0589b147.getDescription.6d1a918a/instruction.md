# Bug Report

### Describe the bug

When swizzling components, the component descriptions are not being displayed correctly. Instead of showing the actual description from the component config, it always falls back to the default `FallbackSwizzleComponentDescription` text.

### Reproduction

1. Set up a theme with components that have custom descriptions in their swizzle config
2. Run the swizzle command to list available components
3. Observe that all components show the fallback description instead of their actual descriptions

Example config:
```js
{
  components: {
    'MyComponent': {
      description: 'This is my custom component description',
      // ... other config
    }
  }
}
```

Expected: Should display "This is my custom component description"
Actual: Always displays the fallback description

### Expected behavior

Components with custom descriptions defined in their config should display those descriptions when running swizzle commands. The fallback description should only be used when no description is provided.

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
