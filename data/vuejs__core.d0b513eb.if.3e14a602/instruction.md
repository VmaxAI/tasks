# Bug Report

### Describe the bug

I'm experiencing an issue where `withDirectives` is not working correctly when used inside render functions. The directives are not being applied to vnodes as expected, and it seems like the function is returning early without processing the directives.

### Reproduction

```js
import { h, withDirectives } from 'vue'

export default {
  render() {
    const vnode = h('div', 'Hello')
    
    // Directives are not being applied
    return withDirectives(vnode, [
      [myDirective, 'some-value']
    ])
  }
}
```

When using `withDirectives` inside a render function (which should be the correct usage), the directives don't get attached to the vnode. The vnode is returned immediately without the directive bindings being set up.

### Expected behavior

The directives should be properly applied to the vnode when `withDirectives` is called inside render functions. The `vnode.dirs` array should contain the directive bindings.

### System Info
- Vue version: 3.x
- Node version: 18.x

---
Repository: /testbed
