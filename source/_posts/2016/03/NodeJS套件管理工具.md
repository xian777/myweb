---
title: NodeJS套件管理工具
tags:
  - NodeJS
date: 2016-03-14 18:55:00
---

<pre># npm介紹

- node package manager
- [npm官網](https://www.npmjs.com/)

# package.json

- $ npm init
<div class="separator" style="clear: both; text-align: center;">
[![](https://4.bp.blogspot.com/-04RgkUsOupM/VuaYTiejJRI/AAAAAAAADrE/aX4I3I-knLcwCvIya7DSSQCtZKVHylqog/s1600/01.png)](https://4.bp.blogspot.com/-04RgkUsOupM/VuaYTiejJRI/AAAAAAAADrE/aX4I3I-knLcwCvIya7DSSQCtZKVHylqog/s1600/01.png)</div>
- [package.json文件](https://docs.npmjs.com/files/package.json)
<div class="separator" style="clear: both; text-align: center;">
[![](https://3.bp.blogspot.com/-9av8Fqm3X4Q/VuaYTuv-KtI/AAAAAAAADrA/5F0Xnq8z5K4e3WGN7SnBrUMLC7YuIdh4A/s1600/02.png)](https://3.bp.blogspot.com/-9av8Fqm3X4Q/VuaYTuv-KtI/AAAAAAAADrA/5F0Xnq8z5K4e3WGN7SnBrUMLC7YuIdh4A/s1600/02.png)</div>
# npm指令

- 安裝資料夾 **node_modules**
``` shell

# 安裝套件
$ npm install -g <package-name>
$ npm install <package-name>

# 安裝並寫入設定檔
$ npm install <package-name> --save
$ npm install **<package-name> --save-dev

# 移除套件
$ npm uninstall -g <package-name>
$ npm uninstall <package-name>

# 搜尋套件
$ npm search <package-name>

# 列出已安裝的套件
$ npm list -g
$ npm list

# 更新套件
$ npm update -g
$ npm update

# 安裝package.json設定檔的套件
$ npm install -l
```</package-name></package-name></package-name></package-name></package-name></package-name></package-name>
</pre>