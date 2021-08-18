If you run this with 

```
yarn webpack serve
```

And take a look at the served js file in the browser.

- Search for `./src/index.js`, that should take you to line 10454
- This is the module code for the index.js
- It has a line `var __webpack_exports__ = {}` at the top. This shadows the `__webpack_exports__` from the startup code:
  ```js
    var __webpack_exports__ = {};
    // This entry need to be wrapped in an IIFE because it need to be in strict mode.
    (() => {
    "use strict";
    var __webpack_exports__ = {};
    /*!**********************!*\
    !*** ./src/index.js ***!
    \**********************/
    __webpack_require__.r(__webpack_exports__);
    /* harmony export */ __webpack_require__.d(__webpack_exports__, {
    /* harmony export */   "default": () => (__WEBPACK_DEFAULT_EXPORT__)
    /* harmony export */ });
    /* harmony default export */ const __WEBPACK_DEFAULT_EXPORT__ = ({
    hello: function hello() {
        console.log('hello');
    }
    });
    })();
  ```
- As a result the export of the umd module ends up being empty