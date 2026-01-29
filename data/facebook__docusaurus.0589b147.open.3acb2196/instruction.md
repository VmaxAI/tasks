# Bug Report

### Describe the bug

I'm experiencing an issue with MDX compilation where nested JSX elements are not being processed correctly. When I have components with multiple levels of nesting, the output seems to be malformed and the component hierarchy gets corrupted.

### Reproduction

```jsx
// Example MDX content
<Outer>
  <Middle>
    <Inner>
      Content here
    </Inner>
  </Middle>
</Outer>
```

When this gets compiled, the nested structure doesn't render properly. The inner components seem to lose their proper parent-child relationships.

### Expected behavior

The MDX compiler should correctly handle nested JSX components and maintain the proper component hierarchy. Each component should receive the correct children and props.

### Additional context

This seems to affect any MDX content with nested custom components. Simple single-level components work fine, but as soon as you introduce nesting (especially 2+ levels deep), things break down.

Using @mdx-js/mdx version 3.0.0.

---
Repository: /testbed
