# Git

## :point_down: よくあるオペレーション

### 既存のリポジトリを作成
```
$ # クローン
$ git clone git@github.com:devhyukke/ToP.git
$
$ # Git Flow 初期化
$ git flow init -d
```

### Git Flow で実施

#### feature 開始
```
$ # 開始元のブランチを最新化
$ git fetch -pt
$
$ git checkout develop
$ git pull --rebase
$
$ # feature を開始
$ git flow feature start branch_name
$
$ # 追跡ブランチでプッシュ
$ git push -u origin HEAD
$ 
$ git branch -a
```

#### feature 更新

##### ブランチを更新
```
$ git fetch -pt
$
$ git checkout feature/branch_name
$
$ git pull --rebase
```

##### リソースをコミット
```
$ # 修正ファイルをステージに追加
$ git add .
$ git status -sb
$
$ # ファイルをコミット＆プッシュ
$ git commit -m "feat: xxxx
$
$ Xxxx"
$
$ git push origin HEAD
```

##### 開始元でリベース
```
$ # 開始元のブランチを最新化
$ git fetch -pt
$
$ git checkout develop
$ git pull --rebase
$
$ # feature に切り替え
$ git checkout feature/branch_name
$
$ # feature をリベース＆強制プッシュ
$ git rebase develop
$
$ git push -f origin HEAD
```

##### 変更をすべて取消
```
$ # 一旦元に戻してやり直したい場合
$ git checkout .
```

#### feature 削除
```
$ git branch -D feature/branch_name
```

### GitHub Flow で実施

#### ブランチ作成
```
$ # 開始元のブランチを最新化
$ git fetch -pt
$
$ git checkout master
$ git pull --rebase
$
$ # ブランチを作成
$ git checkout -b branch_name
$
$ # 追跡ブランチでプッシュ
$ git push -u origin HEAD
$ 
$ git branch -a
```

#### ブランチ更新

##### リソースをコミット
```
$ # 修正ファイルをステージに追加
$ git add .
$ git status -sb
$
$ # ファイルをコミット＆プッシュ
$ git commit -m "feat: xxxx
$
$ Xxxx"
$
$ git push origin HEAD
```

##### 開始元でリベース
```
$ # 開始元のブランチを最新化
$ git fetch -pt
$
$ git checkout master
$ git pull --rebase
$
$ # ブランチ切り替え
$ git checkout branch_name
$
$ # ブランチをリベース＆強制プッシュ
$ git rebase master
$
$ git push -f origin HEAD
```

#### ブランチ削除
```
$ git branch -D branch_name
```

## :memo: よく使うコマンド

### Git Flow
* `git flow init` 初期化する
    * `-d` デフォルトのブランチ名を使用
* `git flow feature start branch_name` feature ブランチを開始する

### リポジトリ
* `git log` コミット変更履歴を参照する
    * `--graph` ツリー表示
    * `--oneline` １行表示
* `git diff HEAD [branch_name]` 最新との変更点を参照する
* `git fetch` リモートのファイルをローカルの追跡ブランチに取得する
    * `-p` `--prune` リモードの無くなったブランチをローカルにも反映
    * `-t` `--tags` リモートのタグをローカルに反映
	* `-a` `--all` すべてを取得
* `git pull [origin] [branch_name]` リモートのファイルをローカルの作業ブランチに取得する
    * `-p` `--prune` リモートの無くなったブランチをローカルにも反映
    * `-t` `--tags` リモートのタグをローカルに反映
	* `--rebase` マージコミットを発生させない
* `git push origin branch_name` ローカルのファイルをリモートに更新する
    * `-f` `--force` ローカルを強制にリモートに反映

### ブランチ
* `git branch` ブランチを確認する
    * `-a` すべて確認
    * `-r` リモートを確認
* `git branch branch_name` ローカルにブランチ作成する
    * `-d` ブランチを削除
    * `-D` ブランチを強制削除
* `git checkout [branch_name]` ローカルでブランチ切り替え
	* `-b` ブランチ作成と同時に切り替え
	* `-b branch_name origin/branch_name` リモートからローカルにブランチ作成と同時に切り替え
* `git rebase branch_name` リベース

### リソース
* `git status` 変更分を確認する
    * `-s` 短い書式で表示
    * `-sb` ブランチ名と短い書式で表示
* `git add [file_name]` インデックスにステージする
	* `.` すべての変更を指定
* `git commit` インデックスにステージされたファイルをコミットする
    * `-m "massage"` メッセージを指定してコミット
    * `--amend` 直前のコミットを修正
* `git reest` インデックスにステージされたファイルを元に戻す
