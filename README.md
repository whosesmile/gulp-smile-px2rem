# gulp-smile-px2rem

Gulpfile.js：

```
var gulp = require('gulp');
var px2rem = require('gulp-smile-px2rem');

gulp.task('px2rem', function () {
  return gulp.src('./**/*.css')
    .pipe(px2rem())
    .pipe(gulp.dest('./dest'));
});
```

### Options

```
px2rem({
    dpr: 2,             // base device pixel ratio (default: 2)
    rem: 32,            // html font-size (default: 32)
    one: false          // whether convert 1px to rem (default: false)
})
```

### Example

#### Pre processing:

One raw stylesheet: `test.css`

```
.selector {
    width: 150px;
    height: 64px; /*px*/
    font-size: 28px; /*px*/
    border: 1px solid #ddd; /*no*/
}
```

#### After processing:

Rem version: `test.debug.css`

```
.selector {
  width: 150px;
  height: 64px;
  font-size: 28px;
  border: 1px solid #ddd;
}
```

@1x version: `test1x.debug.css`

```
.selector {
    width: 75px;
    height: 32px;
    font-size: 14px;
    border: 1px solid #ddd;
}
```

@2x version: `test2x.debug.css`

```
.selector {
    width: 150px;
    height: 64px;
    font-size: 28px;
    border: 1px solid #ddd;
}
```

@3x version: `test3x.debug.css`

```
.selector {
    width: 225px;
    height: 96px;
    font-size: 42px;
    border: 1px solid #ddd;
}
```

## Change Log

### 0.2.2

* Deps: px2rem@~0.4.0
    * The generated [data-dpr] rules follow the origin rule, no longer placed at the end of the whole style sheet.
    * Optimize 0px, do not generate 3 [data-dpr] rules.

### 0.2.1

* Remove deps to vinyl, use gulp-util.
* Enhance test case.

### 0.2.0

* Deps: px2rem@~0.3.0
    * Change default remUnit to 75.
    * Delete comment config.
    * Don't generate @1x, @2x and @3x version stylesheet by default.

### 0.1.9

* Deps: px2rem@^0.2.0
    * Support media query.

### 0.1.8

* Deps: px2rem@~0.1.8
    * Fix regular expression bug and common comments bug which affects rem transformation.

## License

MIT