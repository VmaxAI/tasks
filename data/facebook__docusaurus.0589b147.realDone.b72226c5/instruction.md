# Bug Report

### Describe the bug

I'm encountering an issue with the processor's error handling logic. When processing files, errors are not being properly rejected in certain scenarios, and the success callback seems to be executing in cases where it shouldn't.

### Reproduction

```js
const processor = remark();

// Case 1: When an error occurs without a file
processor.process(invalidInput, (error, file) => {
  // Error should be handled here, but the behavior is inconsistent
  if (error) {
    console.log('Error occurred:', error);
  }
});

// Case 2: Using promise-based approach
processor.process(invalidInput)
  .then(file => {
    // This shouldn't execute when there's an error
    console.log('Success:', file);
  })
  .catch(error => {
    // Error should be caught here
    console.log('Caught error:', error);
  });
```

### Expected behavior

- When an error occurs, it should be properly rejected/passed to the error callback
- The success path should only execute when processing completes successfully
- Promise rejection should work correctly when no callback is provided

### System Info

- remark version: 15.0.1
- Node version: 18.x

The logic for determining when to reject vs. resolve seems inverted or incorrect. This is causing unexpected behavior in error handling workflows.

---
Repository: /testbed
