# cron.logの出力を行う方法

- 環境
  - Ubuntu 18.04.2 LTS

- 手順
  - 50-default.confをオープンする
  ```
  $ sudo -s
  $ vi /etc/rsyslog.d/50-default.conf
  ```

  - 以下のコメントアウトを修正し、保存
  ```
  #cron.*                         /var/log/cron.log
  ```

  - syslogを再起動
  ```
  $ service rsyslog restart
  ```
