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

### 変更履歴 qで終了
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
### 複数コミットをやり直す
git rebase -i [コミットID]
git rebase -i HEAD~3
HEAD~n :1番目の親を指定する。HEADを起点としてn数値分の親コミットまで指定
HEAD^n :マージした場合のn番目の親を指定
修正したいところをpickからeditに修正し、以下のコマンドを入力
git commit --amend (修正コマンド)
git rebase --continue (次へ)



### リモートを表示する(-vでURLも表示)
git remote
git remote -v

### フェッチとプッシュ
フェッチはローカルリポジトリに反映
git fetch [リモート名]

### リモートから情報を取得してマージする
git pull [リモート名] [ブランチ名]
リベース型(merge commitが残らない)
git pull --rebase [リモート名] [ブランチ名]

### プルのリベース型設定
git config --global pull.rebase true
masterブランチのみ
git config branch.master.rebase true

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

### リベース（コミット履歴を一直線にする）
featureとmasterを一直線にする
git checkout [枝分かれしているブランチ名(feature)]
git rebase [親コミットにしたいブランチ名(master)]
git checkout [親コミットにしたいブランチ名(master)]
git merge [枝分かれしているブランチ名(feature)] >>>fast forwardになる

### タグ表示
git tag -l "[パターン]"

###　タグ作成
・注釈付き版（annotated）
git tag -a [タグ名] -m "[メッセージ]"

・軽量版（lightweight）
git tag [タグ名]
後からタグ付け
git tag [タグ名] [コミット名]

### タグの情報表示
git show [タグ名]

### タグ送信
git push [リモート名] [タグ名]
git push origin --tags

### 作業一時避難(コミットしてないステージングしたもの)
git stash
git stash save
避難作業一覧
git stash list
復元
git stash apply
ステージの状況も復元する場合は
git stash apply --index

### 特定の作業復元（0が一番新しい）
git stash apply [スタッシュ名]

### 作業削除
最新
git stash drop
特定のもの
git stash drop [スタッシュ名]
全部
git stash clear