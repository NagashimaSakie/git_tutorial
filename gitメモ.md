$ git config --global user.name "NagashimaSakie"
$ git config --global user.email nagashima@tdc.co.jp
$ git config --global core.editor 'code --wait'
[user]
        name = NagashimaSakie
        email = nagashima@tdc.co.jp
[core]
        editor = code --wait


### ローカルリポジトリの作成
git init

### ステージング
git add .

### コミット
git commit -v
git commit -m "メッセージ（要点、理由）"

### 変更状況
git status

### 変更差分
git diff
git addした後は
git diff --staged

### 変更履歴
git log
git log --oneline
git log -p index.html
git log -n [コミット数]
どのブランチがどのコミットを指すかみる
git log --oneline --decorate

### ファイル削除
git rm ファイル名
git rm -r ディレクトリ名

ファイルを残してgitから削除
git rm --cached ファイル名

### ファイル移動（ファイル名変更）
git mv 旧ファイル 新ファイル

↑は以下操作と同じ効果
mv 旧ファイル
git rm 旧ファイル
git add 新ファイル

### GitHubを追加する
Settings >>> Developer settings >>> Personal access tokens >>> Tokens(classic) >>> Generate new token
アクセストークン：
Your Profile >>> Repositoryies >>> new
…or push an existing repository from the command line
git remote add origin https://github.com/NagashimaSakie/git_tutorial.git
git branch -M main
git push -u origin main

git push リモート名 ブランチ名
git push -u origin master
⇒ポップアップで認証ページが開くので指示に従う

### エイリアス
git config --global alias.ci commit
git config --global alias.[エイリアス名] [コマンド]

### ファイル変更取り消し
git checkout -- [ファイル名]
git checkout -- [ディレクトリ名]
git checkout -- .

### ステージの内容をリポジトリの最新と同期する
git reset HEAD [ファイル名]
git reset HEAD [ディレクトリ名]

### 直前のコミットをやり直す
git commit --amend
リモートリポジトリにPushしたコミットはやり直したらダメ

### リモートを表示する(-vでURLも表示)
git remote
git remote -v

### フェッチとプッシュ
フェッチはローカルリポジトリに反映
git fetch [リモート名]

リモートから情報を取得してマージする
git pull [リモート名] [ブランチ名]

### リモートの情報表示
git remote show [リモート名]

### リモートの変更・削除
git remote rename [旧リモート名] [新リモート名]
git remote rm [リモート名]

### ブランチ
並行して複数機能を開発するためにある
コミットを指すポインタ　スナップショットを切り替える
ブランチの作成、切り替え、マージがバージョン管理ツールより高速

git branch [ブランチ名]
一覧表示
git branch
すべて
git branch -a

### ブランチ切り替え
git checkout [既存ブランチ名]
ブランチを新規作成して切り替え
git checkout -b [新規ブランチ名]

### ブランチ名変更（今いるブランチ）
git branch -m [新ブランチ名]

### ブランチ削除
git branch -d [ブランチ名]
※masterにマージされていない変更が残っている場合削除しない
強制削除は以下
git branch -D [ブランチ名]