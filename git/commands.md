# commands

- コマンド
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
  $ git reset
  $ git reset <ファイル>
  ```

  - コミットする
  ```
  $ git commit -m <commit message>
  ```

  - pushする
  ```
  $ git push -u origin master
  ```