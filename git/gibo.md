# gibo

- 概要
  - .gitignoreを作成することができるコマンドツール

- インストール
  ```
  $ brew install gibo
  ```

- 使い方
  - バージョン確認
    ```
    $ gibo version
    ```

  - ヘルプ
    ```
    $ gibo help
    ```

  - .gitignoreを作成できる対象を表示
    ```
    $ gibo list
    ```

  - .gitignoreの作成（Node用）
    - Node部分は複数指定可能
    ```
    $ gibo dump Node >> .gitignore
    ```