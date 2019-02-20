# WIP（Work In Progress）

- 概要
  - PRでのコードレビュー前に作業者とレビューワーで対応内容を共有しながら、開発を進めて行く開発手法のこと

- メリット
  - レビュー担当者の負担を削減できる
  - 手戻りを少なくできる

- 流れ
  - ブランチを作成する
  - 空コミットをする
  - ブランチをpushする
  - PRを作成する
    - 機能詳細、機能の仕様、実装内容、テスト内容を記載する
  - PRをレビューする
  - 実装をする
  - 変更内容が反映されたブランチをpushする
  - PRを更新し、レビューをする
  - 問題なければ、PRをマージする

- 補足
  - PRはマージできてしまうので、GitHubだろ、「Draft Pull Request」を行うといい

- 参考URL
  - https://qiita.com/numa08/items/b676e38e3dbabfd39d18
  - https://www.publickey1.jp/blog/19/githubwippull_requestdraft_pull_request.html