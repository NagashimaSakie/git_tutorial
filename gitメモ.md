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
