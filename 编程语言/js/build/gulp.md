# gulp

## 一个示例
```js
var gulp = require('gulp');
var concat = require('gulp-concat');//合并
var uglify = require('gulp-uglify');//压缩
var runSequence = require('run-sequence');


gulp.task('default', function() {
    runSequence('watch', 'compile');
});


//watching script change to start default task
gulp.task('watch', function() {
    return gulp.watch([
        'static/js/*.js'
    ], function(event) {
        console.log('File ' + event.path + ' was ' + event.type + ', running tasks...');
        runSequence('compile');
    });
});


gulp.task('compile', function() {
    gulp.src('static/js/*.js')
        .pipe(concat('main.js'))
        .pipe(uglify())
        .pipe(gulp.dest('src/js'));
});
```

## 与webpack集成
