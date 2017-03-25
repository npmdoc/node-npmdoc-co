# api documentation for  [co (v4.6.0)](https://github.com/tj/co#readme)  [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-co.svg)](https://travis-ci.org/npmdoc/node-npmdoc-co)
#### generator async control flow goodness

[![NPM](https://nodei.co/npm/co.png?downloads=true)](https://www.npmjs.com/package/co)

[![apidoc](https://npmdoc.github.io/node-npmdoc-co/build/screen-capture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-co_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-co/build..beta..travis-ci.org/apidoc.html)

![package-listing](https://npmdoc.github.io/node-npmdoc-co/build/screen-capture.npmPackageListing.svg)



# package.json

```json

{
    "bugs": {
        "url": "https://github.com/tj/co/issues"
    },
    "dependencies": {},
    "description": "generator async control flow goodness",
    "devDependencies": {
        "browserify": "^10.0.0",
        "istanbul-harmony": "0",
        "mocha": "^2.0.0",
        "mz": "^1.0.2"
    },
    "directories": {},
    "dist": {
        "shasum": "6ea6bdf3d853ae54ccb8e47bfa0bf3f9031fb184",
        "tarball": "https://registry.npmjs.org/co/-/co-4.6.0.tgz"
    },
    "engines": {
        "iojs": ">= 1.0.0",
        "node": ">= 0.12.0"
    },
    "files": [
        "index.js"
    ],
    "gitHead": "b54d18f8f472ad1314800e786993c4169a5ff9f8",
    "homepage": "https://github.com/tj/co#readme",
    "keywords": [
        "async",
        "flow",
        "generator",
        "coro",
        "coroutine"
    ],
    "license": "MIT",
    "maintainers": [
        {
            "name": "tjholowaychuk",
            "email": "tj@vision-media.ca"
        },
        {
            "name": "jonathanong",
            "email": "jonathanrichardong@gmail.com"
        },
        {
            "name": "jongleberry",
            "email": "jonathanrichardong@gmail.com"
        }
    ],
    "name": "co",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/tj/co.git"
    },
    "scripts": {
        "browserify": "browserify index.js -o ./co-browser.js -s co",
        "prepublish": "npm run browserify",
        "test": "mocha --harmony",
        "test-cov": "node --harmony node_modules/.bin/istanbul cover ./node_modules/.bin/_mocha -- --reporter dot",
        "test-travis": "node --harmony node_modules/.bin/istanbul cover ./node_modules/.bin/_mocha --report lcovonly -- --reporter dot"
    },
    "version": "4.6.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module co](#apidoc.module.co)
1.  [function <span class="apidocSignatureSpan"></span>co (gen)](#apidoc.element.co.co)
1.  [function <span class="apidocSignatureSpan">co.</span>default (gen)](#apidoc.element.co.default)
1.  [function <span class="apidocSignatureSpan">co.</span>wrap (fn)](#apidoc.element.co.wrap)



# <a name="apidoc.module.co"></a>[module co](#apidoc.module.co)

#### <a name="apidoc.element.co.co"></a>[function <span class="apidocSignatureSpan"></span>co (gen)](#apidoc.element.co.co)
- description and source-code
```javascript
function co(gen) {
  var ctx = this;
  var args = slice.call(arguments, 1)

  // we wrap everything in a promise to avoid promise chaining,
  // which leads to memory leak errors.
  // see https://github.com/tj/co/issues/180
  return new Promise(function(resolve, reject) {
    if (typeof gen === 'function') gen = gen.apply(ctx, args);
    if (!gen || typeof gen.next !== 'function') return resolve(gen);

    onFulfilled();

<span class="apidocCodeCommentSpan">    /**
     * @param {Mixed} res
     * @return {Promise}
     * @api private
     */
</span>
    function onFulfilled(res) {
      var ret;
      try {
        ret = gen.next(res);
      } catch (e) {
        return reject(e);
      }
      next(ret);
    }

    /**
     * @param {Error} err
     * @return {Promise}
     * @api private
     */

    function onRejected(err) {
      var ret;
      try {
        ret = gen.throw(err);
      } catch (e) {
        return reject(e);
      }
      next(ret);
    }

    /**
     * Get the next value in the generator,
     * return a promise.
     *
     * @param {Object} ret
     * @return {Promise}
     * @api private
     */

    function next(ret) {
      if (ret.done) return resolve(ret.value);
      var value = toPromise.call(ctx, ret.value);
      if (value && isPromise(value)) return value.then(onFulfilled, onRejected);
      return onRejected(new TypeError('You may only yield a function, promise, generator, array, or object, '
        + 'but the following object was passed: "' + String(ret.value) + '"'));
    }
  });
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.co.default"></a>[function <span class="apidocSignatureSpan">co.</span>default (gen)](#apidoc.element.co.default)
- description and source-code
```javascript
function co(gen) {
  var ctx = this;
  var args = slice.call(arguments, 1)

  // we wrap everything in a promise to avoid promise chaining,
  // which leads to memory leak errors.
  // see https://github.com/tj/co/issues/180
  return new Promise(function(resolve, reject) {
    if (typeof gen === 'function') gen = gen.apply(ctx, args);
    if (!gen || typeof gen.next !== 'function') return resolve(gen);

    onFulfilled();

<span class="apidocCodeCommentSpan">    /**
     * @param {Mixed} res
     * @return {Promise}
     * @api private
     */
</span>
    function onFulfilled(res) {
      var ret;
      try {
        ret = gen.next(res);
      } catch (e) {
        return reject(e);
      }
      next(ret);
    }

    /**
     * @param {Error} err
     * @return {Promise}
     * @api private
     */

    function onRejected(err) {
      var ret;
      try {
        ret = gen.throw(err);
      } catch (e) {
        return reject(e);
      }
      next(ret);
    }

    /**
     * Get the next value in the generator,
     * return a promise.
     *
     * @param {Object} ret
     * @return {Promise}
     * @api private
     */

    function next(ret) {
      if (ret.done) return resolve(ret.value);
      var value = toPromise.call(ctx, ret.value);
      if (value && isPromise(value)) return value.then(onFulfilled, onRejected);
      return onRejected(new TypeError('You may only yield a function, promise, generator, array, or object, '
        + 'but the following object was passed: "' + String(ret.value) + '"'));
    }
  });
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.co.wrap"></a>[function <span class="apidocSignatureSpan">co.</span>wrap (fn)](#apidoc.element.co.wrap)
- description and source-code
```javascript
wrap = function (fn) {
  createPromise.__generatorFunction__ = fn;
  return createPromise;
  function createPromise() {
    return co.call(this, fn.apply(this, arguments));
  }
}
```
- example usage
```shell
...
  console.log(value);
}, function (err) {
  console.error(err.stack);
});
'''

  If you want to convert a 'co'-generator-function into a regular function that returns a promise,
  you now use 'co.wrap(fn*)'.

'''js
var fn = co.wrap(function* (val) {
  return yield Promise.resolve(val);
});

fn(true).then(function (val) {
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
