# alias

- 概要
  - 別名（alias）でTerminalからコマンドを実行できるようにすること

- 方法
  - ~/.bashrcにaliasを記述していく
    - alias [alias]='[command]'

- 手順
  - 設定ファイルをオープンする
  ```
  $ vi ~/.bashrc
  ```

  - 設定ファイルに追記する
  ```
  alias ll='ls -all'
  ```

  - Terminalを終了する
    - 「~/.bashrc」はTerminal起動時に読み込むため、終了→起動しないと追記内容が反映されない
  ```
  $ exit
  ```
