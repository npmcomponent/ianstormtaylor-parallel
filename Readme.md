*This repository is a mirror of the [component](http://component.io) module [ianstormtaylor/parallel](http://github.com/ianstormtaylor/parallel). It has been modified to work with NPM+Browserify. You can install it using the command `npm install npmcomponent/ianstormtaylor-parallel`. Please do not open issues or send pull requests against this repo. If you have issues with this repo, report it to [npmcomponent](https://github.com/airportyh/npmcomponent).*

# parallel

  A simple API for running async functions in parallel.

## Installation

    $ component install ianstormtaylor/parallel
    $ npm install ianstormtaylor/parallel

## Example
  
```js
var parallel = require('parallel');

function getOwner (id, callback) {
  parallel()
    .add(users.get)
    .add(organizations.get)
    .end(id, function (err, results) {
      if (err) return callback(err);
      callback(results[0] || results[1]);
    });
}
```

## API

### #add(fn, [args...])

  Add a `fn` to be called in parallel. Optionally add `args...` specific to the function. Aliased to `push` in case you forget you aren't using [`batch`](https://github.com/visionmedia/batch).

### #bind(context)

  Pass a `context` for all of the functions to be bound with.

### #end([args...], callback)

  Run the functions in parallel and `callback`. Optionally pass in `args...` to be passed to all the functions.

## License

  MIT
