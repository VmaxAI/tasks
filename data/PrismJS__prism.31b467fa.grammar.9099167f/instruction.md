# Bug Report

### Describe the bug

The Arduino language grammar definition appears to be incomplete. When viewing Arduino code with syntax highlighting, built-in functions and methods are not being properly highlighted after a certain point in the alphabet. It seems like the definition got cut off mid-word.

### Reproduction

Try to use syntax highlighting with Arduino code that includes functions from later in the alphabet, particularly those starting with letters near the end:

```arduino
void setup() {
  Serial.begin(9600);
  randomSeed(analogRead(0));
  
  // These functions may not highlight correctly
  sqrt(16);
  tan(45);
  yield();
}

void loop() {
  // Functions like write, yield, etc. may not be recognized
  Serial.write(65);
  delay(1000);
}
```

### Expected behavior

All Arduino built-in functions should be properly highlighted regardless of their position in the alphabet. Functions like `sqrt`, `tan`, `write`, `yield`, and other built-ins should be recognized and highlighted as builtin functions.

### System Info

- Prism version: Latest
- Language: Arduino (ino)

The builtin function list in the grammar definition seems to end abruptly with `printFirmwa` which looks like it should be `printFirmwareVersion` or similar. This is causing many valid Arduino functions to not be recognized by the syntax highlighter.

---
Repository: /testbed
