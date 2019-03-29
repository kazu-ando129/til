# SSHで接続する方法(GitHub)

- 手順
  - 公開鍵と秘密鍵を作成し、権限を設定する
  ```
  $ cd ~/.ssh
  # 以下のコマンドを入力した後、Enterを3回入力する
  $ ssh-keygen -t rsa
  $ chmod 600 id_rsa
  ```

  - configにgithubへHost情報を追記する
  ```
  $ vim ~/.ssh/config
  # 以下を追記
  Host github.com
    HostName github.com
    IdentityFile ~/.ssh/id_rsa
    User git
  ```

  - 作成した公開鍵をリポジトリに設定する
    - リポジトリのsettings→Deploy keys
    - Add deploy keyをクリックし、titleとkeyを入力する
      - keyには「~/.ssh/id_rsa.pub」を入力すること

  - githubへの接続を確認する
  ```
  $ ssh -T git@github.com
  ```