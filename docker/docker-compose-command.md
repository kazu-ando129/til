# docker-composeコマンドのまとめ

- コマンド
  ```
  # build
  $ docker-compose build
  $ docker-compose build <service>

  # up
  $ docker-compose up -d
  $ docker-compose up -d <service>

  # stop
  $ docker-compose stop
  $ docker-compose stop <service>

  # restart
  $ docker-compose restart
  $ docker-compose restart <service>

  # stop & container delete
  $ docker-compose down

  # process
  $ docker-compose ps

  # command
  $ docker-compose exec <service> /bin/bash
  ```