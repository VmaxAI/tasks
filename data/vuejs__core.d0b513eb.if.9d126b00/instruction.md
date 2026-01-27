# Bug Report

### Describe the bug

I'm experiencing an issue with SVG xlink attributes not being handled correctly. When trying to set or remove xlink attributes (like `xlink:href`), the attribute name seems to be getting corrupted or truncated incorrectly.

### Reproduction

```js
const svg = document.createElementNS('http://www.w3.org/2000/svg', 'use')

// Try to set xlink:href attribute
patchAttr(svg, 'xlink:href', '#icon', true)

// The attribute is not set correctly on the element
// Expected: xlink:href="#icon"
// Actual: attribute name is wrong
```

When removing the attribute:
```js
patchAttr(svg, 'xlink:href', null, true)
// The wrong attribute name is being removed
```

### Expected behavior

- When setting `xlink:href` or other xlink attributes, the attribute should be properly set with the correct namespace and name
- When removing xlink attributes (value is null), the correct attribute should be removed from the element
- The xlink prefix should be properly handled when working with the namespace

### System Info

- Vue version: 3.x
- Browser: Chrome/Firefox (both affected)
- Using SVG elements with xlink attributes

This seems to have broken recently, as xlink attributes were working fine before. The issue appears specifically when dealing with SVG elements that use the xlink namespace.

---
Repository: /testbed
