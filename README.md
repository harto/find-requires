find-requires
=============

Searches a Node.js project for "local" module includes (i.e. calls to
`require()` with a relative path), and prints file-dependency pairs to stdout.

The output can be used by tsort(1) to locate circular dependencies.

Example
-------

`a.js`:

    var foo = require('foo')
    var b = require('./b')
    var c = require('./c')
    // ...

`b.js`:

    var bar = require('bar')
    var c = require('./c')
    // ...

`c.js`:

    var baz = require('baz')
    // ...

Output of `find-requires /path/to/project`:

    a.js b.js
    a.js c.js
    b.js c.js

References
----------

 - https://nodejs.org/dist/latest-v4.x/docs/api/modules.html#modules_file_modules
