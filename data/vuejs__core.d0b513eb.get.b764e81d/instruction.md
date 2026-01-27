# Bug Report

### Describe the bug

I'm having an issue with custom elements where accessing declared properties returns `undefined` instead of their actual values. It seems like the getter is not receiving the property key correctly.

### Reproduction

```js
class MyElement extends VueElement {
  static get props() {
    return {
      myProp: String,
      anotherProp: Number
    }
  }
}

customElements.define('my-element', MyElement)

const el = document.createElement('my-element')
el.myProp = 'test value'
el.anotherProp = 42

console.log(el.myProp) // Expected: 'test value', Actual: undefined
console.log(el.anotherProp) // Expected: 42, Actual: undefined
```

### Expected behavior

When accessing a declared property on a custom element instance, it should return the value that was set. The getter should properly retrieve the stored property value.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox

---
Repository: /testbed
