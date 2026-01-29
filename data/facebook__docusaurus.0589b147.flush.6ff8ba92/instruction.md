# Bug Report

### Issue with entity parsing - text content not being captured correctly

I'm encountering a problem with the entity parser where text content seems to be getting lost or not properly captured in the result array. 

### Reproduction
When parsing text with entities, the parsed content is not appearing in the final output as expected:

```js
const parsed = parseEntities('Hello &amp; world', {
  text: (value, position) => {
    console.log('Text:', value); // This logs correctly
  }
});

console.log(parsed); // Expected to contain text segments, but they're missing or empty
```

### Expected behavior
The `result` array should contain all the text segments that were parsed, including the content that was passed to the `text` callback. Currently it seems like the text is being processed but not actually added to the results.

### Additional context
This appears to affect any text content that goes through the flush mechanism. The text callback is being invoked with the correct values, but those values aren't making it into the final parsed result array.

---
Repository: /testbed
