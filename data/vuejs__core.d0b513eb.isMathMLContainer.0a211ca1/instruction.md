# Bug Report

### Describe the bug

I'm experiencing an issue with static nodes during SSR hydration. When a static vnode is being hydrated, it seems like one extra node is being processed than expected, which causes hydration mismatches.

### Reproduction

```js
// Component with static content
const App = {
  template: `
    <div>
      <div>Static 1</div>
      <div>Static 2</div>
      <div>Static 3</div>
    </div>
  `
}

// Server-side render
const html = await renderToString(App)

// Client-side hydration
const container = document.createElement('div')
container.innerHTML = html
hydrate(App, container)
```

When the component contains multiple static nodes that are optimized during build, the hydration process appears to iterate one time too many through the static content nodes. This causes the hydration to grab an extra node that shouldn't be part of the static block.

### Expected behavior

The hydration should only process exactly the number of static nodes that were defined in the vnode's `staticCount` property. It shouldn't process any additional nodes beyond what was originally marked as static.

### System Info
- Vue version: 3.x
- SSR: Yes
- Build optimization: Enabled

This seems to have started happening recently. The issue manifests as hydration warnings in the console about node mismatches, particularly when static content is followed by dynamic content or other components.

---
Repository: /testbed
