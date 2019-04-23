# 自動アップデートの設定確認方法

```bash
$ cat /etc/apt/apt.conf.d/20auto-upgrades
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Unattended-Upgrade "1";
```

- 設定値の意味
  - 1:自動アップデートが有効
  - 0:自動アップデートが無効

- デフォルトの設定
  - デフォルトはセキュリティのアップグレードが行われ、自動再起動は行われない

- 補足
  - unattended-upgrades
    - 自動アップグレードを行うパッケージ