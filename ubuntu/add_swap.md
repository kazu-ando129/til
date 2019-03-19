# スワップ領域の追加方法

- コマンド
  - 1M × 1024（1GB）のスワップ領域の場合
  ```hoge.sh
  $ sudo -s
  # /bin/dd if=/dev/zero of=/var/swap.1 bs=1M count=1024
  # /sbin/mkswap /var/swap.1
  # /sbin/swapon /var/swap.1
  ```
