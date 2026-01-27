# Bug Report

### Describe the bug

I'm experiencing an issue with custom elements where attribute changes are not being properly captured during initialization. When attributes are set on a custom element before it's fully defined, those initial attribute values seem to be lost or not properly synchronized with the component's props.

### Reproduction

```html
<my-custom-element foo="bar" count="42"></my-custom-element>

<script>
import { defineCustomElement } from 'vue'

const MyElement = defineCustomElement({
  props: {
    foo: String,
    count: Number
  },
  setup(props) {
    console.log(props.foo) // Expected: "bar", but might be undefined
    console.log(props.count) // Expected: 42, but might be undefined or string "42"
  }
})

customElements.define('my-custom-element', MyElement)
</script>
```

### Expected behavior

Initial attributes set on the custom element should be properly parsed and available as props when the component mounts. Number-type props should be correctly converted from their string attribute values.

### Additional context

This seems to happen specifically when the custom element has attributes defined in the HTML before the component definition is registered. The attributes exist on the element but don't seem to be processed in time for the initial component setup.

---
Repository: /testbed
