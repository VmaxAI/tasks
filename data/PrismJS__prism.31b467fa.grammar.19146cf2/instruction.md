# Bug Report

### Describe the bug

I'm experiencing an issue with the Stan language syntax highlighting after a recent update. The `#include` directive is no longer being highlighted correctly in my code. Previously, the `#include` statements were properly recognized and styled, but now they appear as plain text.

### Reproduction

```stan
#include "functions.stan"

data {
  int<lower=0> N;
}

model {
  // model code here
}
```

The `#include "functions.stan"` line should be highlighted as a directive/preprocessor statement, but it's not being styled properly anymore.

### Expected behavior

The `#include` directive should be recognized and highlighted with the appropriate styling (as a property/directive). This was working correctly before and is important for code readability when working with modular Stan programs that split functionality across multiple files.

### System Info
- Stan language support version: latest
- Editor: VS Code

---
Repository: /testbed
