# commands

- コマンド

  - リポジトリ作成
  ```
  $ git init
  ```

  - クローンする
  ```
  $ git clone <repo>
  ```

  - リポジトリをを追加
  ```
  $ git remote add origin <repo>
  ```

  - リポジトリの変更内容を確認する
  ```
  $ git status
  ```

  - 変更したファイルをステージングに追加する
  ```
  $ git add <ファイル>
  $ git add .
  ```

  - ステージングから削除する
  ```
  $ git reset <ファイル>
  $ git reset
  ```

  - コミットする
  ```
  $ git commit -m <commit message>
  ```

  - pushする
  ```
  $ git push -u origin master
  ```

  - リモートのURLを確認する
  ```
  $ git remote -v
  ```

  - リモートのURLを設定する
  ```
  $ git remote set-url origin <repo>
  ```
