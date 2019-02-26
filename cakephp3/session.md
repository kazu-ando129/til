# セッションの使い方

## ソースコードの場所
- vendor/cakephp/cakephp/src/Http/Session.php

## セッションの使い方
```Sample.php
// セッションクラスのインスタンス
$session = $this->request->session();

// セッションの有無チェック
// 引数：$name : string|null
// 戻り値：bool（あればtrue）
$session->check($name = null)

// セッションの読み込み
// 引数：$name : string|null
// 戻り値：string or array
$ret = $session->read($name = null)

// セッションの値を読み込み、削除する
// 引数：$name : string
// 戻り値：セッションの値（mixed）、セッションが利用できない場合はnull
$ret = $session->consume($name)

// セッションの書き込み
// 引数：$name : string、$value : mixed
$session->write($name, $value = null)

// セッションの削除
// 引数：$name : string
$session->delete($name)

// すべてのセッション情報を削除
$session->destroy()

// セッションをクリアする
// 引数：$renew ※セッションを更新する場合はtrueにする
$session->clear($renew = false)

// セッションを更新する
$session->renew();

```