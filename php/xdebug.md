# xdebugの設定

- 環境
  - ubuntu 18.04
  - apache2
  - php 7.2
  - Visual Studio Code

- 前提
  - ローカル : ubuntu 18.04
  - リモート : Mac

- 流れ
  1. xdebugをインストールする
  ```
  $ sudo apt-get install php-xdebug
  ```
  2. xdebugの設定をする。以下のコマンドで、ファイルを開き、※1を追記する
  ```
  $ sudo vi /etc/php/7.2/mods-available/xdebug.ini
  ```
  ※1 xdebug.iniに追記する内容
  ```
  xdebug.remote_enable = 1
  xdebug.remote_port = 9000
  xdebug.remote_autostart = 1
  xdebug.remote_host = 123.456.789.000 # MacのIPアドレス
  xdebug.profiler_output_dir = "/tmp"
  xdebug.max_nesting_level= 1000
  ```
  3. Visual Studio Codeに「PHP Debug」の拡張機能をインストールする
  4. 「PHP Debug」の拡張機能の設定をする
     「デバック」→「構成の追加」を選択して、pathMappingsを修正する
      - /var/www/html : ubuntu 18.04側のドキュメントルート
      - /hogehogehoge : Mac側のパス
  ```
    "configurations": [
        {
            "name": "Listen for XDebug",
            "type": "php",
            "request": "launch",
            "port": 9000,
            "stopOnEntry": true,
            "pathMappings": {
                "/var/www/html": "/hogehogehoge"
            }
        },
        {
            "name": "Launch currently open script",
            "type": "php",
            "request": "launch",
            "program": "${file}",
            "cwd": "${fileDirname}",
            "port": 9000
        }
    ]
  ```
