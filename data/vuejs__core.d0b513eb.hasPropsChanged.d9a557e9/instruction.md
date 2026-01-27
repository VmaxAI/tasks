# Bug Report

### Describe the bug

Component is not re-rendering when props are updated. I have a parent component passing props to a child component, and when the parent updates those props, the child component doesn't update even though the prop values have changed.

### Reproduction

```js
// Parent component
const ParentComponent = {
  setup() {
    const message = ref('initial')
    
    const updateMessage = () => {
      message.value = 'updated'
    }
    
    return { message, updateMessage }
  },
  template: `
    <div>
      <ChildComponent :message="message" />
      <button @click="updateMessage">Update</button>
    </div>
  `
}

// Child component
const ChildComponent = {
  props: ['message'],
  template: '<div>{{ message }}</div>'
}
```

When clicking the button, the child component still displays "initial" instead of "updated". The prop value changes in the parent but the child doesn't receive the update.

### Expected behavior

The child component should re-render and display the updated prop value when the parent changes it.

### System Info
- Vue version: 3.x
- Browser: Chrome 121

---
Repository: /testbed
