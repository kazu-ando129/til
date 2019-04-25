# RewriteCond

- 概要
  - mode_writeの構文
  - RewriteCondはRewriteRuleの前に記述する
  - RewriteCondの条件が正となった場合、RewriteRuleに沿って処理される
  - RewriteCondは複数指定可能、複数指定した場合、ANDもしくはOR条件を指定できる
  - RewriteRuleは複数指定可能、複数指定した場合、RewriteCondが正となれば、RewriteRuleがすべて処理される

- 例
```
RewriteEngine on
RewriteCond %{HTTP_HOST} ^hoge\.co\.jp$
RewriteRule ^(.*)$ http://○○○.com/$1 [R=301,L]
```