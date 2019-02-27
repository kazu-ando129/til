# eager load（イーガーロード）

- 概要
  - N+1問題を解決するために、リレーション先のデータをin句でまとめてとってくること

- N+1問題とは
  - 全てのデータ（A）の取得に1回 + （A）の文だけのN個のSQLを発行してしまう問題
  - テーブルの関係が「users : posts = 1 : 多」となっている場合、
    postsのデータを元に繰り返し、usersに対してSQLを発行すると、起こる

- 補足
  - CakePHP3だと、ORMでfindを使用する際に、containを使用し、
    関連データをロード（イーガーロード）することで、N+1問題を回避する

- 参考
  https://book.cakephp.org/3.0/ja/orm/retrieving-data-and-resultsets.html#contain