# キャッシュ

- HTTPキャッシュの種類
  - ローカルキャッシュ
    - ブラウザが実行されている端末で保持するキャッシュのこと
  - シェアードキャッシュ
    - ブラウザとオリジンサーバの間のプロキシサーバなどのWebサーバーで保持するキャッシュのこと
      - プライベートな情報は保持していない

- HTTPキャッシュ以外
  - 独自キャッシュ（以下、例）
    - クエリの実行結果のキャッシュ
    - 動的に生成されたHTMLの断面のキャッシュ

- Webアプリケーションが配信するキャッシュの種類
  - ナビゲーションリソース
    - HTMLやAPIのレスポンス
  - 静的リソース
    - CSS、JavaScript、画像など

- HTTPキャッシュの制御
  - Cache-Controlレスポンスヘッダーで制御する
    - Cache-Control : public, max-age=604800
      - 公開されたもの（public）だから、そのキャッシュは604800秒（7日間）は有効という意味
    - public以外にprivate、no-storeを設定できる
      - private : シェアードキャッシュに保持したくないとき
      - no-store : キャッシュしたくないとき
        - 更新頻度が高いときに使用するとよい
    - max-age以外にs-maxageがあり、シェアードキャッシュにおいてはmax-ageより優先される
    - Cache-Control : immutable
      - 更新されない不変のリソースを表す
      - むやみに設定できないので、気をつけること
  - Expiress
    - 絶対的なキャッシュを保持する日時を設定する
    - Cache-Controlが設定されている場合は、Cache-Controlが優先される

- HTTPキャッシュ有効によるオリジンサーバからのHTTPレスポンス
  - 有効な場合、304 Not Modified
  - 無効な場合、200 OK

- 参考
  https://developer.mozilla.org/ja/docs/Web/HTTP/Headers/Cache-Control