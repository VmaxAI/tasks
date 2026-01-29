# Bug Report

### Describe the bug

Theme component aliases are not being created correctly. When trying to use theme components, the first component in the theme is being skipped and not registered as an alias. Additionally, the original theme aliases (prefixed with `@theme-original`) are being created when they shouldn't be.

### Reproduction

1. Create a custom theme with multiple components
2. Try to import the first component from the theme using its alias
3. The component is not found/accessible
4. Also notice that `@theme-original` aliases are being created even when `addOriginalAlias` is false

For example, if your theme has components:
```
- ComponentA.tsx
- ComponentB.tsx  
- ComponentC.tsx
```

Only ComponentB and ComponentC will be aliased and accessible. ComponentA will be missing from the webpack aliases.

### Expected behavior

All theme components should be properly aliased and accessible via their `@theme/` prefixed imports. The `@theme-original` aliases should only be created when `addOriginalAlias` is true (for swizzled components).

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
