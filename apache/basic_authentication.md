# Basic認証を設定する

- 前提
  - sudo -sで管理者に昇格しておくこと

- 手順
  1. Apacheをインストールする
  2. Apacheのmod rewriteを有効にする
  ```
  # /usr/sbin/a2enmod rewrite
  ```
  3. apache.confを更新する（AllowOverride None→AllowOverride All）
  ```
  # vi /etc/apache2/apache2.conf
  <Directory /var/www/>
    Options Indexes FollowSymLinks
    #AllowOverride None
    AllowOverride All
    Require all granted
  </Directory>
  ```
  4. apacheを再起動する
  ```
  # service apache2 restart
  ```
  5. .htpasswdを作成して、ユーザー情報を追記し、ドキュメントルートに配置する
  ```
  hoge:hsoaveaivfbiaievbiy
  ```
  6. htaccessにBasic認証の設定を追記する（AuthGroupFileは記述しない。エラーとなる
  ```
  AuthType Basic
  AuthName      "Authentication required"
  AuthUserFile  【フルパス】/.htpasswd
  #AuthGroupFile /dev/null
  Require       valid-user
  ```
