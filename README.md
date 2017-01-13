GULP inline-base64
==================

This helper will inject images into your css files.

```
background-image: inline_image('images/base64/logo-bottom.png');
```

Install it
----------

```
npm install --save-dev gulp-inline-base64
```

Use it
------

In css change ``url('path/to/image')`` to ``inline_image('path/to/image')``

Here is my sass config. 

```
var sass = require('gulp-sass'),
	inline_base64 = require('gulp-inline-base64'),
	autoprefixer = require('gulp-autoprefixer');
...

// SASS
gulp.task('sass', function() {
    return gulp.src([
        path_src + '/css/**/*.scss',
        '!' + path_src + '/css/**/_*.scss'
    ])
    .pipe(sass({
        includePaths: [
            path_src + '/css/',
            'bower_components/',
        ],
        imagePath: path_src
    }))
    .pipe(inline_base64({
        baseDir: path_src,
        debug: true
    }))
    .pipe(autoprefixer("last 2 version", "> 1%", {
        cascade: true
    }))
    .pipe(gulp.dest(path_tmp + '/css'))
});
```

Options
-------
 - ``baseDir`` : the root path for assets
 - ``useRelativePath`` : overrides baseDir; root path is relative to the input file's directory
 - ``debug`` : show debug messages


```