# Bug Report

### Describe the bug

When using `<svg>` elements inside MathML `<annotation-xml>` tags, the SVG namespace is not being applied correctly. The SVG content is being treated as HTML instead of being rendered in the proper SVG namespace.

### Reproduction

```html
<math>
  <annotation-xml>
    <svg>
      <circle cx="50" cy="50" r="40" />
    </svg>
  </annotation-xml>
</math>
```

### Expected behavior

The `<svg>` element inside `<annotation-xml>` should be recognized and rendered in the SVG namespace (Namespaces.SVG), allowing proper rendering of SVG content within MathML annotations.

### Actual behavior

The SVG element is not being properly namespaced, causing rendering issues with SVG content embedded in MathML annotation-xml elements.

### System Info
- Vue version: 3.x
- Browser: Latest Chrome/Firefox

---
Repository: /testbed
