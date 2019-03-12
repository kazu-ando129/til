# cron

- 使い方
  - 動作しているかの確認（Active: active (running)と表示されれば、動作している）
  ```
  $ sudo service cron status
  ```

  - 起動する
  ```
  $ sudo service cron start
  ```

  - 再起動する
  ```
  $ sudo service cron restart
  ```

  - cronの登録
  ```
  $ crontab -e
  ```

  - crontabの書き方
  ```
  0 2 * * * ls -all
  ```

  - 左から、分、時、日、月、曜日となる
    - 分：0〜59
    - 時：0〜23
    - 日：1〜31
    - 月：1〜12
    - 曜日：月（1）〜日（7または0）
　- 指定方法
    - リスト：1,2,3,4,5
    - 範囲：1-5
    - 共存：1,2,4-6
    - 間隔：*/10（分で設定したときは、10分間隔となる）