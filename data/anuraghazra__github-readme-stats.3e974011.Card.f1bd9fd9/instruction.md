# Bug Report

### Describe the bug

I'm experiencing an issue with the card rendering where the gradient stops are not being distributed correctly. When using multiple gradient colors, the visual appearance is off and the gradient doesn't look smooth across the entire card.

### Reproduction

```js
const card = new Card({
  colors: {
    gradient: ['ff0000', '00ff00', '0000ff']
  }
});

// The gradient rendering looks incorrect
// The color stops are not evenly distributed
```

When I create a card with 3 gradient colors, the spacing between the color stops appears wrong. For example, with 3 colors, I'd expect stops at 0%, 50%, and 100%, but they seem to be calculated incorrectly.

### Expected behavior

The gradient should smoothly transition between all specified colors with evenly distributed stops. For a 3-color gradient, the stops should be at 0%, 50%, and 100%.

### Additional context

This affects the visual appearance of cards with multiple gradient colors. The gradient looks compressed or incorrectly distributed.

---
Repository: /testbed
