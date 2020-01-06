# MySQL 8ユーザーのパスワード更新

```
$ FLUSH PRIVILEGES;
$ ALTER USER 'root'@'localhost' IDENTIFIED BY '新しいパスワード';
```