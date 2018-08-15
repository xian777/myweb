---
title: gulp 前端最佳化js和css工具
tags:
  - NodeJS
date: 2016-03-14 21:40:00
---

<div>安裝gulp-cli套件 </div><div><pre class="brush:bash">$ npm install gulp-cli -g</pre>

</div><div>安裝gulp套件 </div><div><pre class="brush:bash">$ npm install gulp --save-dev</pre>

</div><div>安裝gulp plugin套件 </div><div><pre class="brush:bash">$ npm install gulp-concat
$ npm install gulp-cssmin
$ npm install gulp-uglify
$ npm install rimraf</pre>
</div><div>新增gulpfile.js </div><div><pre class="brush:javascript">/// &lt;binding BeforeBuild='min' Clean='clean' /&gt;
"use strict";

var gulp = require("gulp"),
    rimraf = require("rimraf"),
    concat = require("gulp-concat"),
    cssmin = require("gulp-cssmin"),
    uglify = require("gulp-uglify");

var paths = {
    webroot: "./wwwroot/"
};

paths.js = paths.webroot + "js/**/*.js";
paths.minJs = paths.webroot + "js/**/*.min.js";
paths.css = paths.webroot + "css/**/*.css";
paths.minCss = paths.webroot + "css/**/*.min.css";
paths.concatJsDest = paths.webroot + "assets/site.min.js";
paths.concatCssDest = paths.webroot + "assets/site.min.css";

gulp.task("clean:js", function (cb) {
    rimraf(paths.concatJsDest, cb);
});

gulp.task("clean:css", function (cb) {
    rimraf(paths.concatCssDest, cb);
});

gulp.task("clean", ["clean:js", "clean:css"]);

gulp.task("min:js", function () {
    return gulp.src([paths.js, "!" + paths.minJs], { base: "." })
        .pipe(concat(paths.concatJsDest))
        .pipe(uglify())
        .pipe(gulp.dest("."));
});

gulp.task("min:css", function () {
    return gulp.src([paths.css, "!" + paths.minCss])
        .pipe(concat(paths.concatCssDest))
        .pipe(cssmin())
        .pipe(gulp.dest("."));
});

gulp.task("min", ["min:js", "min:css"]);
gulp.task("default", function () {
    gulp.watch(paths.js, function () {
        gulp.run("min:js");
    });
    gulp.watch(paths.css, function () {
        gulp.run("min:css");
    });
});</pre>

</div><div>執行工作 </div><div><pre class="brush:bash">$ gulp clean
$ gulp min</pre>

</div><div><div class="separator" style="clear: both; text-align: center;">[![](https://3.bp.blogspot.com/-vdOW4ShjPTg/Vua-53hG9qI/AAAAAAAADrU/qY1yB9rkhFQ9m7niKIVoAuDjF8TLc8CLA/s1600/01.png)](https://3.bp.blogspot.com/-vdOW4ShjPTg/Vua-53hG9qI/AAAAAAAADrU/qY1yB9rkhFQ9m7niKIVoAuDjF8TLc8CLA/s1600/01.png)</div></div>