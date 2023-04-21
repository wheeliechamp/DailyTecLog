## < SQL >

### SQLPLUSをBATで呼び出して、結果をCSVに出力する方法
+ test_1.bat を作成
```
SQLPLUS [LoginID_1]/[LoginPass_1]@[接続IP]:[Port番号]/[SID] @test_1.sql "arg_1"
SQLPLUS [LoginID_2]/[LoginPass_2]@[接続IP]:[Port番号]/[SID] @test_1.sql "arg_2"

※ LoginPassに%が含まれる場合は%%とする。
```
+ test_1.sql を作成
```
SET echo off
SET linesize 3000
SET pagesize 0
SET trimspool on
SET feedback off
SET colsep ','
spool C:\temp\IAP_&1..csv
SELECT * FROM 作業時間;
spool off
exit
```
+ BAT呼び出し
```
①作成したファイルを同じフォルダに置いて
②コマンドプロンプト起動
③test_1.batを実行
④DB上のテーブルから値を取得しファイルに出力される
```