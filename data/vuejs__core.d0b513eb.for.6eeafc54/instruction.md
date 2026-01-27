# Bug Report

### Describe the bug

When using custom elements with scoped styles and slotted content, the `:slotted` CSS selector doesn't work correctly for nested elements within slots. The scoped style attributes are being applied in the wrong order, causing the root element of the slotted content to not receive the scoped ID attribute before its children are processed.

### Reproduction

```js
// Define a custom element with scoped styles
const MyElement = defineCustomElement({
  template: `
    <div>
      <slot></slot>
    </div>
  `,
  styles: [`
    :slotted(.item) {
      color: red;
    }
    :slotted(.nested) {
      font-weight: bold;
    }
  `]
})

customElements.define('my-element', MyElement)

// Use it with nested slotted content
const container = document.createElement('div')
container.innerHTML = `
  <my-element>
    <div class="item">
      <span class="nested">Nested content</span>
    </div>
  </my-element>
`
```

### Expected behavior

The scoped style attributes should be applied to both the root slotted element and all its descendants, allowing `:slotted` styles to work correctly for nested elements. The root element should receive the scoped ID before processing its children.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox

---
Repository: /testbed
