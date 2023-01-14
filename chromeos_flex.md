# 情報技術の知見に関する履歴

## < ChromeOs Flex >
### 公式
+ https://chromeenterprise.google/intl/ja_jp/os/chromeosflex/
+ [インストールガイド](https://support.google.com/chromeosflex/answer/11552529?hl=ja&visit_id=638087373823997548-1542311112&ref_topic=11551271&rd=1)
+ [ショートカットキー](https://support.google.com/chromebook/answer/183101?hl=ja)


### < 参考 >
+ [ChromeOS Flex ショートカットキー](https://4thsight.xyz/41777)
+ [Flutter開発環境構築](http://pineplanter.moo.jp/non-it-salaryman/2022/02/07/chromebook-flutter/)
+ [Kindleで本を読む](https://zenn.dev/junkawa/articles/chromeosflex_install_kindleforpc#crostini-%E7%92%B0%E5%A2%83)
  + 補足
  1. [Wineを設定](https://wiki.winehq.org/Debian)
      + Preparation を実行
        + $ sudo dpkg --add-architecture i386 
      + Add the repository を実行
        + $ sudo mkdir -pm755 /etc/apt/keyrings
        + $ sudo wget -O /etc/apt/keyrings/winehq-archive.key https://dl.winehq.org/wine-builds/winehq.key
  1. Dockerfile 拡張子なしでファイルを作成
      + wget 〜 winehq-archive.key https://dl.winehq.org/wine-builds/winehq.key のPathをWine設定(/etc/apt/keyrings)で置き換える
  1. ディレクトリに格納し、ターミナルでディレクトリに移動
  1. sudo docker build -t kindle_img ./ を実行
  1. 現在のユーザをDockerグループに追加
      + [Linuxでグループ確認](https://kazmax.zpp.jp/linux_beginner/etc_group.html)
      + whoamiで確認
      + $ sudo gpasswd -a user docker で追加
  1. docker_kindle でコンテナ起動
  1. フォントインストール
+ [Wineインストール](https://pc.watch.impress.co.jp/docs/column/nishikawa/1442374.html)
+ [Ubuntu で Wine7 を使って Kindle を読む](https://qiita.com/nanbuwks/items/a8f3b558cae92e5576bf)
+ [Ubuntu 21.10にKindleをインストール](https://qiita.com/relu/items/8fc87a895e17609012aa)
+ [xhost](https://kledgeb.blogspot.com/2012/09/ubuntu-x-2.html) 
+ Linuxファイルをインストールするときは、Linuxファイルの下にファイルを格納→右クリック→Linuxでのインストールを実行