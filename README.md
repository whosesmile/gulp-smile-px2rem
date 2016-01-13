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

Rem version: `test.css`

```
  @media screen and (max-width:980px) {
    #header { max-width: 750px; box-shadow: 0 0 1px #ddd; }
  }
  @media only screen and (min-device-width:241px) and (max-device-width:360px) {
    #header { max-width: 750px; box-shadow: 0 0 1px #ddd; }
  }
  .selector { width: 150px; height: 64px; font-size: 28px; border: 1px solid #ddd; }
```