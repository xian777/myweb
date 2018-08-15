---
title: Nginx run as windows service
tags:
  - gogs
  - nginx
date: 2016-08-15 21:09:00
---

在[官網下載Nginx](https://nginx.org/en/download.html)編譯好的執行檔
<div class="separator" style="clear: both; text-align: center;">[![](https://3.bp.blogspot.com/-8vknH_NDWWc/V7G-1WbRz9I/AAAAAAAAD2U/8dIR2IfcZLE0Gg8h6v5JraGoPmztkHwNQCLcB/s1600/01.png)](https://3.bp.blogspot.com/-8vknH_NDWWc/V7G-1WbRz9I/AAAAAAAAD2U/8dIR2IfcZLE0Gg8h6v5JraGoPmztkHwNQCLcB/s1600/01.png)</div><div>
</div><div>[下載nssm](https://nssm.cc/download)用來把nginx的執行檔註冊成一個服務</div><div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-smMH3K8Qmqw/V7G-1QMgHrI/AAAAAAAAD2Q/eueu5aJVMdsHgtocc-YkiZLhNUHOm86ugCLcB/s1600/02.png)](https://2.bp.blogspot.com/-smMH3K8Qmqw/V7G-1QMgHrI/AAAAAAAAD2Q/eueu5aJVMdsHgtocc-YkiZLhNUHOm86ugCLcB/s1600/02.png)</div><div>
</div><div>執行nssm install nginx</div><div>設定好nginx執行檔的路徑和工作目錄</div><div class="separator" style="clear: both; text-align: center;">[![](https://1.bp.blogspot.com/-x_sQIDUaHcs/V7G-1Z_m1bI/AAAAAAAAD2M/X1KZotWYxuglW7JQ7GHok9H4sT09JVG9ACLcB/s1600/03.png)](https://1.bp.blogspot.com/-x_sQIDUaHcs/V7G-1Z_m1bI/AAAAAAAAD2M/X1KZotWYxuglW7JQ7GHok9H4sT09JVG9ACLcB/s1600/03.png)</div><div>
</div><div>啟動nginx服務</div><div class="separator" style="clear: both; text-align: center;">[![](https://3.bp.blogspot.com/--lOAGgATX0c/V7G-10HDnZI/AAAAAAAAD2Y/lE0r7P2DHYw0mMJiW-XSd_xLm_-BtdaGwCLcB/s1600/04.png)](https://3.bp.blogspot.com/--lOAGgATX0c/V7G-10HDnZI/AAAAAAAAD2Y/lE0r7P2DHYw0mMJiW-XSd_xLm_-BtdaGwCLcB/s1600/04.png)</div><div>
</div><div>nginx啟動成功</div><div class="separator" style="clear: both; text-align: center;">[![](https://3.bp.blogspot.com/-Yik38hLCppY/V7G-16Q0rQI/AAAAAAAAD2c/RZz1ARt3dhspgMuzP6N-3sDtI7LmGlJpQCLcB/s1600/05.png)](https://3.bp.blogspot.com/-Yik38hLCppY/V7G-16Q0rQI/AAAAAAAAD2c/RZz1ARt3dhspgMuzP6N-3sDtI7LmGlJpQCLcB/s1600/05.png)</div><div>
</div><div>
</div>