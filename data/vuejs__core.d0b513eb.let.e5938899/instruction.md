# Bug Report

### Describe the bug
I'm encountering an issue where static nodes are not being removed correctly from the DOM. When a component with static content is unmounted, some DOM elements remain in the tree instead of being fully cleaned up.

### Reproduction
```js
const App = {
  template: `
    <div v-if="show">
      <span>Static content</span>
      <span>More static content</span>
    </div>
  `,
  data() {
    return {
      show: true
    }
  }
}

// Toggle show to false
app.show = false
// Expected: all elements removed
// Actual: some elements still present in DOM
```

### Expected behavior
When toggling off a component with static nodes, all associated DOM elements should be completely removed from the document. Currently, it appears that the last element before the anchor is not being properly removed.

### System Info
- Vue version: 3.x
- Browser: Firefox/Chrome

This seems to affect components with multiple static child nodes. Single static nodes appear to work fine.

---
Repository: /testbed
