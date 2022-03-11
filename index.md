# 情報技術の知見に関する履歴

## kotkin + Android
## Flutter + Android
### Flutterのインストール

## Rust + RaspberryPi
## 調べたこと
### SQL
+ Oracle DUAL について
  + Oracleで利用できるダミーテーブル。FROM句で使える。
  + SELECT 'Dummy' FROM DUAL; のような利用ができる。
+ Oracle DUAL を PosgreSQL で
  + SELECT 'Dummy'; だけで良い。FROM句なくてもいけるんだ。
### プログラミングを学べるドローン
+ https://www.robolink.com/products/codrone
+ https://www.kickstarter.com/projects/robolink/codrone-edu-the-drone-designed-for-the-classroom?lang=ja

### 気になった記事
+ [ウクライナ巡るサイバー空間の攻防-ロシアの-控えめな攻撃-に驚く声も-そのワケは](https://www.msn.com/ja-jp/news/world/%E3%82%A6%E3%82%AF%E3%83%A9%E3%82%A4%E3%83%8A%E5%B7%A1%E3%82%8B%E3%82%B5%E3%82%A4%E3%83%90%E3%83%BC%E7%A9%BA%E9%96%93%E3%81%AE%E6%94%BB%E9%98%B2-%E3%83%AD%E3%82%B7%E3%82%A2%E3%81%AE-%E6%8E%A7%E3%81%88%E3%82%81%E3%81%AA%E6%94%BB%E6%92%83-%E3%81%AB%E9%A9%9A%E3%81%8F%E5%A3%B0%E3%82%82-%E3%81%9D%E3%81%AE%E3%83%AF%E3%82%B1%E3%81%AF/ar-AAUUFLU?ocid=msedgntp)
## 良く忘れること
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
