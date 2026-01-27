# Bug Report

### Describe the bug

I'm encountering an issue with boolean attributes in templates. When setting a boolean attribute to an empty string `''`, it's not being included in the rendered output as expected.

### Reproduction

```js
// Template with boolean attribute set to empty string
<button disabled="">Click me</button>

// Or in render function
h('button', { disabled: '' }, 'Click me')
```

The `disabled` attribute should be present in the DOM when set to an empty string (as per HTML spec where `<button disabled="">` is equivalent to `<button disabled>`), but it's being removed from the element.

### Expected behavior

According to HTML specifications, boolean attributes with empty string values should be treated as `true` and included in the rendered output. For example:
- `<select multiple="">` should render with the `multiple` attribute
- `<input disabled="">` should render with the `disabled` attribute

Currently these attributes are being stripped out when the value is an empty string.

### System Info
- Vue version: 3.x

---
Repository: /testbed
