# lodash.template-async

The [Lodash](https://lodash.com/) method `_.template` exported as a [Node.js](https://nodejs.org/) module.

Patched to compile an async functions when the new option `isAsync` is
set to `true`. If this option is not provided or it is set to `false`, it behaves
exactly like the original [lodash.template](https://www.npmjs.com/package/lodash.template).

Useful if you need/want to use await inside your templates.

Currently tracking lodash version `4.17.21`.

Built and published from:
[https://github.com/hMihaiDavid/lodash/tree/4.17-async-template-npm](https://github.com/hMihaiDavid/lodash/tree/4.17-async-template-npm)

This change is awaiting review, merge and release in official lodash repo:
[https://github.com/lodash/lodash/pull/6017](https://github.com/lodash/lodash/pull/6017)

When (if?) the pull request gets merged AND the feature is released in lodash,
this package will be deprecated. It will still be usable BUT a deprecation
message will appear when installing it, recommending to use the upstream lodash.


```bash
$ npm i --save lodash.template-async
```

```js
import template from 'lodash.template-async';

const compiled = template('<% print(await Promise.resolve(val)) %>', { isAsync: true })
console.log(await compiled({ 'val': 42 })); // => '42'
```

or, in a `script` and not a `module`:

```js
const template = require('lodash.template-async');
const compiled = template('<% print(await Promise.resolve(val)) %>', { isAsync: true })

async function main() {
  console.log(await compiled({ 'val': 42 })); // => '42'
}

main();
```

For more options, see the [documentation](https://lodash.com/docs#template).

Credits to the original authors and contributors to lodash.

This package is unofficial and is  NOT affiliated with lodash,
the lodash maintainers or the OpenJS foundation.

Following is a copy of the lodash `LICENSE` file.

```
Copyright OpenJS Foundation and other contributors <https://openjsf.org/>

Based on Underscore.js, copyright Jeremy Ashkenas,
DocumentCloud and Investigative Reporters & Editors <http://underscorejs.org/>

This software consists of voluntary contributions made by many
individuals. For exact contribution history, see the revision history
available at https://github.com/lodash/lodash

The following license applies to all parts of this software except as
documented below:

====

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

====

Copyright and related rights for sample code are waived via CC0. Sample
code is defined as all source code displayed within the prose of the
documentation.

CC0: http://creativecommons.org/publicdomain/zero/1.0/

====

Files located in the node_modules and vendor directories are externally
maintained libraries used by this software which have their own
licenses; we recommend you read them, as their terms may differ from the
terms above.
```
