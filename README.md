# npmdoc-co

#### basic api documentation for  [co (v4.6.0)](https://github.com/tj/co#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-co.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-co) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-co.svg)](https://travis-ci.org/npmdoc/node-npmdoc-co)

#### generator async control flow goodness

[![NPM](https://nodei.co/npm/co.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/co)

- [https://npmdoc.github.io/node-npmdoc-co/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-co/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-co/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-co/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-co/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-co/build/screenCapture.npmPackageDependencyTree.svg)



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
            "name": "tjholowaychuk"
        },
        {
            "name": "jonathanong"
        },
        {
            "name": "jongleberry"
        }
    ],
    "name": "co",
    "optionalDependencies": {},
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
    "version": "4.6.0",
    "bin": {}
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
