# Bug Report

### Describe the bug

I'm encountering an issue with the SFC compiler where import statements are throwing parsing errors. When I try to use ES6 imports in my script blocks, the compiler fails with syntax errors even though the import syntax is valid.

### Reproduction

```vue
<script>
import { ref } from 'vue'
import MyComponent from './MyComponent.vue'

export default {
  components: { MyComponent }
}
</script>
```

When compiling this component, I get a parsing error complaining about the import statements. The error message indicates that the imports are not being recognized as valid syntax.

### Expected behavior

The compiler should correctly parse ES6 module syntax including import/export statements in script blocks. This used to work fine in previous versions.

### Additional context

This seems to have started happening recently. I'm not sure if this is related to a recent change in how the compiler handles script parsing, but it's blocking my ability to use standard module imports in Vue SFCs.

---
Repository: /testbed
