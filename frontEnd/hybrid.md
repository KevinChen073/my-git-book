JSBridge：https://juejin.im/post/5abca877f265da238155b6bc
- native调用JS：window对象调用
- JS调用Native：注入API 或者是url schema的拦截

注入 API 方式的主要原理是，通过 WebView 提供的接口，向 JavaScript 的 Context（window）中注入对象或者方法，让 JavaScript 调用时，直接执行相应的 Native 代码逻辑，达到 JavaScript 调用 Native 的目的。
