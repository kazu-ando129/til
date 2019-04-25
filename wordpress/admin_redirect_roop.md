
# 管理画面にアクセスしたときにリダイレクトループが発生

- 概要
  - リバースプロキシ環境だと、発生する
  - 事象が発生したのは、ALBにてHTTPをHTTPSにリダイレクトしていた環境

- 対策
```wp-config.php
・
・
define('FORCE_SSL_ADMIN', true);
if ( ! empty( $_SERVER['HTTP_X_FORWARDED_PROTO'] ) && $_SERVER['HTTP_X_FORWARDED_PROTO'] == 'https' ) {
        $_SERVER['HTTPS']='on';
}

require_once(ABSPATH . 'wp-settings.php');
```

- 参考リンク
  [管理画面での SSL 通信](https://wpdocs.osdn.jp/%E7%AE%A1%E7%90%86%E7%94%BB%E9%9D%A2%E3%81%A7%E3%81%AE_SSL_%E9%80%9A%E4%BF%A1)