# Bug Report

### Describe the bug

When calling `getDescription()` for theme components in the swizzle command, the function returns incorrect descriptions. It seems like the description is being fetched for the wrong component, causing mismatched or fallback descriptions to be displayed.

### Reproduction

```js
// When swizzling a component, the description shown doesn't match the actual component
// For example, trying to get description for component 'Footer' might return 
// the description for a completely different component or the fallback description

const components = await getThemeComponents({...});
const description = getDescription('Footer'); 
// Returns wrong description or fallback instead of Footer's actual description
```

### Expected behavior

`getDescription()` should return the correct description for the component name that's passed as an argument. Each component should display its own description, not a fallback or description from another component.

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
