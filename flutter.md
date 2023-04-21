# [情報技術の知見に関する履歴](./index.md)

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
1. DerviceManager/Actionsで[WipeData]を実行

### FlutterでWebViewを使う
+ pubspec.yaml に追記し、[Pub get]クリック
```
dev_dependencies:
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

### Flutter/Dart 仕様
+ future
+ print(), debugPrint()

## < 参考ページ >
+ [miniSdkVersionエラー](https://it-dxblog.com/flutter-error-min-sdk/)
+ [path_provider](https://qiita.com/kurararara/items/2cf891ccc6bae039233f)
+ [WebView](https://pub.dev/packages/webview_flutter)