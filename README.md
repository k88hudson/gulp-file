# gulp-file

[![Build Status](https://secure.travis-ci.org/alexmingoia/gulp-file.png)](http://travis-ci.org/alexmingoia/gulp-file) 
[![NPM version](https://badge.fury.io/js/gulp-file.png)](http://badge.fury.io/js/gulp-file)

Create vinyl files from a string or buffer and insert into the Gulp pipeline.

## Installation

```sh
npm install gulp-file
```

## API

### plugin(name, source)

Creates a vinyl file with the given `name` from `source` string or buffer and
returns a transform stream for use in your gulp pipeline.

## Example

[Primus][0] outputs the client library as a string. Using `gulp-file` we can
create a vinyl file from the string and insert it into the gulp pipeline:

```javascript
var gulp = require('gulp')
  , file = require('gulp-file');

gulp.task('js', function() {
  var str = primus.library();

  return file('primus.js', str).pipe(gulp.dest('dist'));
});
```

You can use it in the middle of your pipeline as well:

```javascript
var gulp = require('gulp')
  , file = require('gulp-file');

gulp.task('js', function() {
  var str = primus.library();

  return gulp.src('scripts/**.js')
    .pipe(file('primus.js', str))
    .pipe(gulp.dest('dist'));
});
```

## BSD Licensed

[0]: https://github.com/primus/primus
