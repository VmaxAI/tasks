# Bug Report

### Describe the bug

I'm experiencing an issue with component props compilation where properties are not being merged correctly. When a component has multiple prop bindings that should be merged together, the resulting compiled output seems to be missing the expected property values.

### Reproduction

```vue
<template>
  <MyComponent 
    static-prop="value"
    :dynamic-prop="someValue"
    v-bind="spreadProps"
  />
</template>
```

When compiling this template, the static and dynamic props that should be included in the merge arguments appear to be getting lost. The compiled output doesn't contain all the expected properties.

### Expected behavior

All props (static, dynamic, and spread) should be properly merged and included in the final props object passed to the component. The compiler should create a merged props expression that contains all property definitions.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

This seems to have started happening recently. The props object being passed to the component is incomplete compared to what's defined in the template.

---
Repository: /testbed
