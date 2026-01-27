# Bug Report

### Describe the bug

The application crashes with a syntax error after the latest update. It looks like there's some Python code that got accidentally committed into the JavaScript codebase in `lib/context.js`. The `cookies` setter was replaced with a Python function definition.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  // Attempting to set cookies causes a syntax error
  ctx.cookies = someCookieObject;
  ctx.body = 'Hello World';
});

app.listen(3000);
```

When running the server, I get a syntax error because the code is trying to parse Python syntax in a JavaScript file.

### Expected behavior

The cookies setter should work normally and allow setting the cookies object on the context without any errors.

### System Info
- Node version: 18.x
- OS: macOS

This seems to have broken basic functionality. The entire file won't parse due to the syntax error.

---
Repository: /testbed
