# Bug Report

### Describe the bug

I'm experiencing an issue where text content in elements is not being updated correctly during re-renders. When a component updates and the new text content is the same as the old text content, the element's text is being cleared instead of kept as-is.

### Reproduction

```js
const { createApp, h, ref } = Vue

const App = {
  setup() {
    const text = ref('Hello')
    
    const update = () => {
      // Trigger re-render with same text value
      text.value = 'Hello'
    }
    
    return () => h('div', { onClick: update }, text.value)
  }
}

createApp(App).mount('#app')
```

Steps to reproduce:
1. Create a component that renders text content
2. Trigger an update where the new text is identical to the previous text
3. The text disappears from the DOM instead of staying the same

### Expected behavior

When the text content hasn't actually changed (same string value), it should remain visible in the element. The DOM text node should not be modified unnecessarily.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox

This seems like a regression as this was working fine before. The text content should only be cleared when it's actually different or when switching from text to other types of children.

---
Repository: /testbed
