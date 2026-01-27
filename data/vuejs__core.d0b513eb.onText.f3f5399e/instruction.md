# Bug Report

### Describe the bug

I'm encountering an issue with HTML entity decoding in text content within templates. It seems like HTML entities (like `&amp;`, `&lt;`, etc.) are not being decoded properly in certain scenarios, or they're being decoded when they shouldn't be.

### Reproduction

```vue
<template>
  <div>
    <p>This text contains &amp; entity</p>
    <span>Another &lt;example&gt; here</span>
  </div>
</template>
```

When rendering this template, the entities either remain encoded when they should be decoded, or the decoding behavior is inconsistent across different tag contexts.

### Expected behavior

HTML entities in text content should be consistently decoded and displayed correctly in the rendered output. For example, `&amp;` should render as `&` and `&lt;` should render as `<`.

### Additional context

This might be related to how the parser handles text nodes in different contexts (script tags vs regular content). The behavior seems to have changed recently and is causing rendering issues in my application.

---
Repository: /testbed
