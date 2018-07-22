Info
----

A lighter version of [mv](https://www.npmjs.com/package/mv) without the support for directory moving between devices (directory moving within same device works as well as files between devices).

This means this project has no dependancy to [rimraf](https://www.npmjs.com/package/rimraf) or [ncp](https://www.npmjs.com/package/ncp) making it a lot lighter and smaller.

Usage:
------

```js
var mv = require('mv-lite');

mv('source/file', 'dest/file', function(err) {
  // done. it tried fs.rename first, and then falls back to
  // piping the source file to the dest file and then unlinking
  // the source file.
});
```

Another example:

```js
mv('source/dir', 'dest/a/b/c/dir', {mkdirp: true}, function(err) {
  // done. it first created all the necessary directories, and then
  // tries fs.rename
});
```

Another example:

```js
mv('source/file', 'dest/file', {clobber: false}, function(err) {
  // done. If 'dest/file' exists, an error is returned
  // with err.code === 'EEXIST'.
});
```
