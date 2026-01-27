# Bug Report

### Describe the bug

The `customClass` plugin is not applying class mappings when only a `mapper` function is provided without an `adder` function. The class transformation logic seems to be skipped entirely in this scenario.

### Reproduction

```js
Prism.plugins.customClass.mapper = (className) => {
  return `custom-${className}`;
};

// Highlight some code
const html = Prism.highlight('const x = 1;', Prism.languages.javascript, 'javascript');

// Expected: Classes should be prefixed with 'custom-'
// Actual: Original class names are used without transformation
```

### Expected behavior

When a `mapper` function is configured, all token classes should be transformed according to the mapper, regardless of whether an `adder` function is present or not. The mapper should apply to all classes in the `env.classes` array.

### System Info
- Prism version: latest
- Browser: N/A (affects all environments)

---
Repository: /testbed
