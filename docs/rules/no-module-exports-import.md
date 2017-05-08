# no-module-exports-import

Reports the use of CommonJS exports with import declarations in modules.

Based on the [no-import-module-exports rule](https://github.com/benmosher/eslint-plugin-import/pull/804) created by Thomas Marek.

## Options

#### `exceptions`
 - An array of globs. The rule will be omitted from any file that matches a glob
   in the options array. For example, the following setting will omit the rule
   in the `some-file.js` file.

```json
"enact/no-module-exports-import": ["error", {
    "exceptions": ["**/*/some-file.js"]
}]
```

## Rule Details

### Fail

```js
import { stuff } from 'starwars'
module.exports = thing

import * as allThings from 'starwars'
exports.bar = thing

import thing from 'other-thing'
exports.foo = bar

import thing from 'starwars'
const baz = module.exports = thing
console.log(baz)
```

### Pass

```js
import thing from 'other-thing'
export default thing

const thing = require('thing')
module.exports = thing

const thing = require('thing')
exports.foo = bar

import thing from 'otherthing'
console.log(thing.module.exports)

// in some-file.js
// eslint import/no-import-module-exports: ["error", {"exceptions": ["**/*/some-file.js"]}]
import foo from 'path';
module.exports = foo;
```

### Further Reading
 - [webpack issue #4039](https://github.com/webpack/webpack/issues/4039)
