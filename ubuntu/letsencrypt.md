# Let's Encrypt

- 概要
  - 無料SSL
  - 3ヶ月更新

- 前提
  - ubuntu
  - apache 2系をインストールしておく
    - mod sslを有効にしておく
  - gitをインストールしておく

- 使い方
  - 管理者に切り替える
  ```
  $ sudo -s
  ```

  - mod sslが有効か確認する
    - 「Module ssl already enabled」と表示されればOK
  ```
  # a2enmod ssl
  ```

  - 作業ディレクトリに移動する
  ```
  # cd /usr/local/
  ```

  - gitからダウンロードする
  ```
  # git clone https://github.com/certbot/certbot
  ```

  - certbotに異動する
  ```
  # cd certbot
  ```

  - 証明書を発行する
    - [document root] : ドキュメントルートのパス
    - [domain] : SSL証明書を発行するドメイン（-d にて複数可能）
    - [email] : 連絡先のEmailアドレス
  ```
  # ./certbot-auto certonly --webroot --webroot-path [document root] -d [domain] -m [email]
  ```

  - Apacheに証明書を設定する
    - 証明書に関連するファイルは以下に出力される（logは参照する）
      - pem :  /etc/letsencrypt/live/[domain]/fullchain.pem
      - key :  /etc/letsencrypt/live/[domain]/privkey.pem
    - /etc/apache2/sites-available/default-ssl.confの以下を変更する
      - SSLCertificateFile : /etc/letsencrypt/live/[domain]/fullchain.pem
      - SSLCertificateKeyFile : /etc/letsencrypt/live/[domain]/privkey.pem

  - 設定ファイルを読み込む
  ```
  # service apache2 reload
  ```

  - cronで自動更新の設定
    - 以下を追記（毎週、月曜日の3時に更新）
    - 0 3 * * 1 /usr/local/certbot/certbot-auto renew --post-hook "service apache2 restart"
  ```
  # crontab -e
  ```
