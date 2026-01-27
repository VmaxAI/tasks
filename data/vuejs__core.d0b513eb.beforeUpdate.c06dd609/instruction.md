# Bug Report

### Describe the bug

I'm experiencing an issue with `v-model` on radio buttons where the checked state doesn't update properly when the bound value changes. The radio button remains in its previous state even though the underlying data has been updated.

### Reproduction

```vue
<template>
  <div>
    <input type="radio" v-model="selected" value="option1" />
    <input type="radio" v-model="selected" value="option2" />
    <button @click="changeSelection">Change to option2</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selected: 'option1'
    }
  },
  methods: {
    changeSelection() {
      this.selected = 'option2'
      // The second radio button should be checked now, but it's not updating
    }
  }
}
</script>
```

### Expected behavior

When the `selected` value changes from 'option1' to 'option2', the second radio button should become checked and the first one should become unchecked. The UI should reflect the current state of the bound data.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox

This seems to have started happening recently. The radio buttons work fine on initial render but don't update when the model value changes programmatically.

---
Repository: /testbed
