# 情報技術の知見に関する履歴

## < kotkin + Android >
## < Flutter >
### 公式
+ https://flutter.dev/
+ https://flutter.github.io/samples/#
+ https://gallery.flutter.dev/#/
### Flutterのインストール
+ https://flutter.dev/ から
+ [Get started] ⇒ Install 画面で
+ Get the Flutter SDK をダウンロード
+ zipを解凍しフォルダに展開、環境変数でflutter\binにPATHを通す

### AndroidStudioでFlutterを利用する設定
+ Welcom to Android Studioの画面で[Plugins]をクリック
+ Marketplaceで[Flutter]と[Dart]をインストールする 

### pubspec.yaml の書き方 (AndroidStudio)
+ 公式
  + https://dart.dev/tools/pub/dependencies#version-constraints
+ Versionの調べ方
  + pubspec.yaml を開く 
  + Packageを記載
  + [Pub outdated]クリック
  + 表示内容は下記
    + Current(現Ver) 、Upgradable(UpGrade可能なVer)、Resolvable、Latest(最新Ver β含む) 

### AndroidStudioで既存プロジェクトがエラーとなる場合の対処
1. dartファイルを開き、[Get dependencies]を実行する。
1. PrjExplorerで pubspec.yaml を開き[pub get]を実行。
   + Project Structure
       + Project Settings/Project
           + ProjectSDK が <No SDK> となっているので、選択
       + Modules
           + Dependencies ModuleSDK を選択
1. DeviceManager/Actionsで[WipeData]を実行

### FlutterでWebViewを使う
+ pubspec.yaml に追記し、[Pub get]クリック
```
dependencies:
  webview_flutter: ^3.0.1
```
+ main.dart に追記
```
import 'package:webview_flutter/webview_flutter.dart';

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(widget.title),
      ),
      body: const WebView(
        initialUrl: 'https://yahoo.co.jp',
        userAgent: '',
        javascriptMode: JavascriptMode.unrestricted,
      ),
```
### FlutterでTimer処理（周期実行）
+ 参考：https://api.flutter.dev/flutter/dart-async/Timer/Timer.periodic.html
```
Timer.periodic(
    // 10秒毎に実行
    Duration(seconds: 10),
    (timer) {
      // 実行したいメソッド
    }
);
```

### FlutterでWindowsDesktopアプリ作成環境 (2022-04-07)
1. VisualStudio 2022 をC++によるデスクトップ開発を選択してインストール
2. コマンドラインで実行
```
  > flutter config --enable-windows-desktop
```
3. AndroidStudioで[New Flutter Project]を選択
4. Platformsの[Windows]を選択

### FlutterでWindowsDesktopアプリをリリースビルドする(2022-04-13)
1. プロジェクトを作成して
2. コマンドラインで実行
```
  > flutter build windows --release
```
3. build¥windows¥runner¥Release¥"アプリ名".exe が作成される

### Flutter/WebView

### Flutter/Dart 仕様
+ future
+ print(), debugPrint()
 
## < Rust + RaspberryPi >

## <Java >

### JAVA_HOME の確認方法
+ cmd で > echo %JAVA_HOME% を実行

### Java Code Snippet
+ 年月文字列から月初日、月末日の文字列を取得する
  ```
  import java.time.LocalDateTime;
  import java.time.format.DateTimeFormatter;
 
    String dt = "2020-06";
    LocalDateTime firstDay = LocalDateTime.of(
      Integer.parseInt(dt.split("-")[0]),
      Integer.parseInt(dt.split("-")[1]), 1, 0, 0);
    LocalDateTime lastDay = firstDay.plusMonths(1).plusDays(-1);
    DateTimeFormatter dtf = DateTimeFormatter.ofPattern("yyyy-MM-dd");
    System.out.println(firstDay.format(dtf));
    System.out.println(lastDay.format(dtf));
  ```

+ 現在の日付にn日加減算する
  ```
  import java.util.*;
  Calendar curcal = Calendar.getInstance();
  curcal.add(Calendar.DATE, -30);
  System.out.println(curcal.get(Calendar.YEAR));
  System.out.println(curcal.get(Calendar.MONTH));
  System.out.println(curcal.get(Calendar.DAY));
  ```

+ Listをカンマ区切りの文字列にする。Base64Encode
```
import java.util.*;

public class Main {
    public static void main(String[] args) throws Exception {
        // Your code here!
        List<String> aaa = new ArrayList<String>();
        aaa.add("aaa");
        aaa.add("bbb");
        
        String str = String.join(",", aaa);
        System.out.println(str);
        
        
        String bbb = Base64.getEncoder().encodeToString("%涼風%".getBytes(StandardCharsets.UTF_8));
        System.out.println(bbb);
        
    }
}
```

+ ListのEmpty、空判定(2022-06-13) 
```
  List<String> tmp = new ArrayList<String>();
  tmp.add("AAA");
  System.out.println(tmp.isEmpty());
```

## < Eclipse >
+ SVNで比較するときに文字化けする。
  + [ウィンドウ]⇒[設定]⇒[一般]⇒[コンテンツタイプ]
  + コンテンツタイプのいずれか選択
  + ファイルの関連付け（不足なら追加）
  + デフォルトエンコードを設定（UTF-8など）し、[更新]
  + 適用して閉じる

## < SQL >
### Oracle DUAL について
+ Oracleで利用できるダミーテーブル。FROM句で使える。
+ SELECT 'Dummy' FROM DUAL; のような利用ができる。
+ Oracle DUAL を PosgreSQL で
  + SELECT 'Dummy'; だけで良い。FROM句なくてもいけるんだ。

### PostgreSql
+ テーブルにコメント
  + COMMENT ON TABLE t_nm IS 't_nmという名のテーブル';
+ カラムにコメント
  + COMMENT ON COLUMN t_nm.column_nm IS 'column_nmという名のカラム';
+ カラム名修正
  + ALTER TABLE t_nm RENAME COLUMN c_nm_old TO c_nm_new;
+ データ型変更(varchar⇒integer)
  + ALTER TABLE t_nm ALTER COLUMN c_nm TYPE integer USING "c_nm"::integer;
+ インデックス追加
  + CREATE INDEX i_c_nm_idx1 ON t_nm (c_nm);
+ 現在日付：SELECT current_date
+ 現在日時：SELECT noe()
+ 現在日時の 30日後
  + SELECT now() + CAST('30 days' AS INTERVAL);
+ 現在日時の 1ヶ月後
  + SELECT now() + CAST('1 months' AS INTERVAL);

### Docker
+ コマンド
  + docker ps     実行中コンテナを一覧表示
  + docker ps -a  停止中も含めて一覧表示
  + docker restart container_name コンテナ再起動

### VSCode
+ [日付ショートカットの設定](https://qiita.com/umyu/items/d9c3875133b8d1c6cb20) (2022-04-07)

### Slack
+ リマインダー設定
  + メッセージフィールドで、/remind [@someone or #channel] でできる。

## < Windows >
+ Androidスマホのテザリングが使えないときの対処
  + デバイスマネージャで、Remote NDIS Compatible Device に！が表示されている
    + 設定/ネットワークとインターネット/状態/ネットワークのリセット を実行
 
## < 気になった記事やページ >
+ [スマホをノートPC化](https://www.mirabook.info/)
+ [Python再帰呼び出し](https://atmarkit.itmedia.co.jp/ait/articles/2203/17/news011.html)
+ [ウクライナ巡るサイバー空間の攻防-ロシアの-控えめな攻撃-に驚く声も-そのワケは](https://www.msn.com/ja-jp/news/world/%E3%82%A6%E3%82%AF%E3%83%A9%E3%82%A4%E3%83%8A%E5%B7%A1%E3%82%8B%E3%82%B5%E3%82%A4%E3%83%90%E3%83%BC%E7%A9%BA%E9%96%93%E3%81%AE%E6%94%BB%E9%98%B2-%E3%83%AD%E3%82%B7%E3%82%A2%E3%81%AE-%E6%8E%A7%E3%81%88%E3%82%81%E3%81%AA%E6%94%BB%E6%92%83-%E3%81%AB%E9%A9%9A%E3%81%8F%E5%A3%B0%E3%82%82-%E3%81%9D%E3%81%AE%E3%83%AF%E3%82%B1%E3%81%AF/ar-AAUUFLU?ocid=msedgntp)
+ [Googleアカウントのプライバシー 行動履歴のダダ漏れ防ぐには](https://www.msn.com/ja-jp/news/techandscience/google%E3%82%A2%E3%82%AB%E3%82%A6%E3%83%B3%E3%83%88%E3%81%AE%E3%83%97%E3%83%A9%E3%82%A4%E3%83%90%E3%82%B7%E3%83%BC-%E8%A1%8C%E5%8B%95%E5%B1%A5%E6%AD%B4%E3%81%AE%E3%83%80%E3%83%80%E6%BC%8F%E3%82%8C%E9%98%B2%E3%81%90%E3%81%AB%E3%81%AF/ar-AAV1eoz?ocid=msedgntp#page=2)
+ [プログラミングを学べるドローン](https://www.robolink.com/products/codrone)
+ [プログラミングを学べるドローン](https://www.kickstarter.com/projects/robolink/codrone-edu-the-drone-designed-for-the-classroom?lang=ja)


## < 良く忘れること >
### git command
+ ユーザー名とメールアドレスの設定（コミット時の記録用）
  + git config --global user.name "UserName"
  + git config --global user.mail "UserMail"
+ git設定の確認
  + git config --global --list（--local, --system）
+ git設定の削除
  + git config --global --unset user.name
+ remoteリポジトリがある状態で、ローカルにリポジトリを作成 
+ フォルダを作成して 
  + git init を実行（.git が作成される） 
+ remoteリポジトリを追加 
  + git remote add origin (Url) (originは好きなのでOK) 
+ pullする 
  + git pull origin develop (developブランチをpullする)
  + git pull のみだと、最新のブランチをpull 
  + $ git fetch origin master
+ pull で上書きする
  1. git fetch origin master
  2. git reset --hard origin/master
+ branch作成 
  + git branch -a (ブランチ一覧をみる) 
  + git checkout develop (ブランチ元に切り替える) 
  + git checkout -b feature/### (###でブランチ名を指定して作成) 
  + git push -u origin feature/### (ブランチをリモートに登録) 
+ Urlのリモートリポジトリをクローンする 
  + git clone Url 
+ ステージング 
  + git add "ファイル名" でcommitするファイルをステージング 
+ ステージングファイルの確認 
  + git status （緑色で表示されたのがステージングされているファイル） 
+ commit 
  + git commit -m "コメント" （ステージングファイルをコミット） 
  + git commit "ファイル名" 
  + git commit . 変更したファイル全てをコミット 
+ commit 取り消し 
  + git reset --soft HEAD^ 直前のコミットだけなかったことにする 
  + git reset --hard HEAD^ 直前のコミットとファイルを元に戻す 
+ push 
  + git push origin feature/### 
+ merge 
  + merge元ブランチに移動してからマージする 
+ git checkout develop （developに移動） 
+ git merge feature/### （developにfeature/###をマージ） 
+ log 
  + git log -1 最新の１件のコミットを確認 
+ リモートのブランチを確認 
  + git fetch リモートのブランチ情報をローカルに反映 
  + git branch -a でブランチのリスト表示 
+ リモートブランチ削除 
  + git push --delete origin "branch name"
+ git clone で "SSL certificate problem: self signed certificate" エラーとなる
  + git config --global http.sslVerify false を実行する
  + [参考](https://qiita.com/yazzy/items/3dae25b3cb8042eed8c2)
+ プロジェクトをgit repository に登録する
  + git でremote repository を作成し、URLを取得
  + プロジェクトで git init
  + git add .
  + git commit -m "first commit"
  + git push -u origin master


```markdown
Syntax highlighted code block
# Header 1
## Header 2
### Header 3
- Bulleted
- List
1. Numbered
2. List
**Bold** and _Italic_ and `Code` text
[Link](url) and ![Image](src)
```

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
