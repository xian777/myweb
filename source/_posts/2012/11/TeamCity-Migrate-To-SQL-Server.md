---
title: TeamCity Migrate To SQL Server
tags:
  - Build Server
  - Migrate
  - SQL Server
  - TeamCity
date: 2012-11-08 20:57:00
---

## 首先淮備好資料庫，例如一個名稱為TeamCity的DB
![](http://2.bp.blogspot.com/-vkJGa93mgS8/UJud6ZDutdI/AAAAAAAAAXA/efJdpGCptNE/s1600/01.NewDB.png)](http://2.bp.blogspot.com/-vkJGa93mgS8/UJud6ZDutdI/AAAAAAAAAXA/efJdpGCptNE/s1600/01.NewDB.png)

## 建一個登入帳號，這裡帳號用bar，密碼用foo當範例
![](http://1.bp.blogspot.com/-WRh2WZcEgNM/UJud7G_MGSI/AAAAAAAAAXI/hipvEg4ZmNY/s1600/02.NewUser.png)](http://1.bp.blogspot.com/-WRh2WZcEgNM/UJud7G_MGSI/AAAAAAAAAXI/hipvEg4ZmNY/s1600/02.NewUser.png)

## 給予db_owner的權限
![](http://3.bp.blogspot.com/-1mkS-zvnKaw/UJud7voFGwI/AAAAAAAAAXQ/IbcM34MqW_g/s1600/03.Owner.png)](http://3.bp.blogspot.com/-1mkS-zvnKaw/UJud7voFGwI/AAAAAAAAAXQ/IbcM34MqW_g/s1600/03.Owner.png)

## 再來下載Database Driver，官網的文件中有介紹兩種Driver
## 但我試了半天都不行用，後來爬文找到更改連線字串的寫法就可以了
## 所以在這裡以Microsoft JDBC Driver來介紹
## 先去Microsoft Download Center [下載Driver](http://www.microsoft.com/zh-tw/download/details.aspx?id=11774)
![](http://1.bp.blogspot.com/-YNHb9XrRv9k/UJud8PN0l0I/AAAAAAAAAXY/-w8b5MtUqSk/s1600/04.Download.png)](http://1.bp.blogspot.com/-YNHb9XrRv9k/UJud8PN0l0I/AAAAAAAAAXY/-w8b5MtUqSk/s1600/04.Download.png)

## 下載後解壓縮，把sqljdbc4.jar複製到這個神秘的地方
![](http://3.bp.blogspot.com/-whQq072tXfw/UJud8vAsOII/AAAAAAAAAXg/QhDweQyvu08/s1600/05.LibDir.png)](http://3.bp.blogspot.com/-whQq072tXfw/UJud8vAsOII/AAAAAAAAAXg/QhDweQyvu08/s1600/05.LibDir.png)

## 再來編輯database.mssql.properties.dist這一個範本檔
![](http://1.bp.blogspot.com/-8eIjxlciydI/UJud9RDp2bI/AAAAAAAAAXo/LzrW7FDwNZA/s1600/06.DatabaseTemplate.png)](http://1.bp.blogspot.com/-8eIjxlciydI/UJud9RDp2bI/AAAAAAAAAXo/LzrW7FDwNZA/s1600/06.DatabaseTemplate.png)

## 官網的文件是把帳密打在後面，但試了半天就是不行
[爬文的結果](http://t800t8.blogspot.tw/2009/07/configuring-teamcity-with-sql-server.html)把帳密改寫在連線字串中就成功了，JAVA真是一種神秘的語言
![](http://2.bp.blogspot.com/-k2IyAF5GUFk/UJud91XM0HI/AAAAAAAAAXw/l4Jxv5E89a8/s1600/07.Config.png)](http://2.bp.blogspot.com/-k2IyAF5GUFk/UJud91XM0HI/AAAAAAAAAXw/l4Jxv5E89a8/s1600/07.Config.png)

TeamCity升級到7.1.2後，JDBC的設定不能用了，只好再試了一下另一種連線方式jtds-1.2.2
首先到此下載，[jTDS - SQL Server and Sybase JDBC driver](http://sourceforge.net/projects/jtds/files/)
我下載最新的版本，會有java.lang.UnsupportedClassVersionError的錯誤，換成1.2.2就好了
一樣把jtds-1.2.2.jar複製到lib/jdbc的資料夾
連線字串就可以照著範本的格式打了
```xml
connectionUrl=jdbc:jtds:sqlserver://<hostname>:1433/<dbname>
connectionProperties.user=<username>
connectionProperties.password=<password>
```

## 參考資料
* [Migrating to an External Database](http://confluence.jetbrains.net/display/TCD7/Migrating+to+an+External+Database)

## 到此淮備工作就完成了，要開始轉移資料之前，要先把服務停下來
![](http://1.bp.blogspot.com/-ZO21PE08jw8/UJud-TBJl6I/AAAAAAAAAX4/3I9MMVD7KMw/s1600/08.StopService.png)](http://1.bp.blogspot.com/-ZO21PE08jw8/UJud-TBJl6I/AAAAAAAAAX4/3I9MMVD7KMw/s1600/08.StopService.png)

## 然後打開一個cmd，輸入以下指令
```shell
set path=%path%;c:\TeamCity\jre\bin
```

這行是和設定JAVA_HOME這個神秘的全域變數同樣的效果
用來把Java Run Time的路徑包含進系統的path
因為我沒安裝JAVA環境，所以要指向到TeamCity自帶的jre路徑
但如果在執行過程中會發生無法開啟jvm.cfg這個錯誤訊息的話
把System32下面的Java.exe、Javaw.exe、Javaws.exe都砍掉就行了
```shell
maintainDB.cmd migrate -T c:\ProgramData\JetBrains\TeamCity\config\database.mssql.properties.dist
```

maintainDB.cmd是TeamCity自帶的資料庫維護工具，可以用來備份、還原、和搬移資料
這邊用的是migrate，把剛設定資料庫的設定檔用-T參考傳進去就行了
![](http://3.bp.blogspot.com/-6skME4p2u5U/UJud-95UhjI/AAAAAAAAAYA/L0Lezi6GN14/s1600/09.Cmd.png)](http://3.bp.blogspot.com/-6skME4p2u5U/UJud-95UhjI/AAAAAAAAAYA/L0Lezi6GN14/s1600/09.Cmd.png)

順利的話，就會開始搬移資料進SQL Server，並且也會把剛剛的資料庫連線範本
複制成正式用的檔案database.properties
![](http://3.bp.blogspot.com/-Y76ZKXqUFmY/UJumBkLtVVI/AAAAAAAAAYw/56KfkQqXhIQ/s1600/10.Success.png)](http://3.bp.blogspot.com/-Y76ZKXqUFmY/UJumBkLtVVI/AAAAAAAAAYw/56KfkQqXhIQ/s1600/10.Success.png)

## 資料庫的物件也都建好了，重啟服務就完成囉
[![](http://2.bp.blogspot.com/-D0C-bR5Sb1Y/UJueAvRMlHI/AAAAAAAAAYQ/JzHxo2Gdqvw/s1600/11.MigrateOK.png)](http://2.bp.blogspot.com/-D0C-bR5Sb1Y/UJueAvRMlHI/AAAAAAAAAYQ/JzHxo2Gdqvw/s1600/11.MigrateOK.png)

## 參考資料
* [Microsoft JDBC Driver 4.0 for SQL Server](http://www.microsoft.com/zh-tw/download/details.aspx?id=11774)
* [Error: could not open `C:/Program Files/Java/jre6/lib/i386/jvm.cfg'之解决方法](http://blog.csdn.net/xiaofeixia22222/article/details/6235720)
* [Configuring TeamCity with SQL Server 2008 Express](http://t800t8.blogspot.tw/2009/07/configuring-teamcity-with-sql-server.html)
* [Migrating TeamCity database to Microsoft SQL Server 2008 R2](http://www.tellingmachine.com/post/Migrating-TeamCity-database-to-Microsoft-SQL-Server-2008-R2.aspx)
* [Migrating to an External Database](http://confluence.jetbrains.net/display/TCD7/Migrating+to+an+External+Database)