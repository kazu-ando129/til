# output_branch_diff

- 概要
  - カレントブランチとmasterブランチの差分を_diff.zipに出力するコマンド

- 前提
  - カレントブランチをチェックアウトしておくこと

- コマンド
  ```
  $ git archive --format=zip --prefix=_diff/ HEAD `git diff master --diff-filter=ACMR --name-only` -o _diff.zip
  ```

- 参考
  https://qiita.com/hirosco/items/84849ed8fd91da6aae05