


PC_User@DESKTOP-L6BC1VA MINGW64 ~
$ git config --global user.name "NagashimaSakie"

PC_User@DESKTOP-L6BC1VA MINGW64 ~
$ git congig --global user.email nagashima@tdc.co.jp
git: 'congig' is not a git command. See 'git --help'.

The most similar command is
        config

PC_User@DESKTOP-L6BC1VA MINGW64 ~
$ git config --global user.email nagashima@tdc.co.jp

PC_User@DESKTOP-L6BC1VA MINGW64 ~
$ git config --global core.editor 'code --wait'

PC_User@DESKTOP-L6BC1VA MINGW64 ~
$ ^C

PC_User@DESKTOP-L6BC1VA MINGW64 ~
$

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
git log oneline
git log -p index.html
git log -n [コミット数]

ファイル削除
git rm ファイル名
git rm -r ディレクトリ名

ファイルを残してgitから削除
git rm --cached ファイル名