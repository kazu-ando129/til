# チェックボックスの操作方法のまとめ

```test.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>checkbox sample</title>
</head>
<body>
  <p class="checked">チェック済みは：</p>
  <p><label for="1"><input id="1" type="checkbox" name="hoge[]" value="1">あいうえお</label></p>
  <p><label for="2"><input id="2" type="checkbox" name="hoge[]" value="2">かきくけこ</label></p>
  <p><label for="3"><input id="3" type="checkbox" name="hoge[]" value="3">さしすせそ</label></p>
  <p><label for="4"><input id="4" type="checkbox" name="hoge[]" value="4">たちつてと</label></p>
  <button type="button" class="btn-get-check">チェック済みを表示</button>
  <button type="button" class="btn-set-all-check">すべてチェック</button>
  <button type="button" class="btn-set-all-un-check">チェック解除</button>
  <button type="button" class="btn-set-reverse-check">チェックを反転</button>
  <button type="button" class="btn-set-2-check">かきくけこだけチェック/解除</button>
  <script src="http://code.jquery.com/jquery-3.3.1.min.js"
    integrity="sha256-FgpCb/KJQlLNfOu91ta32o/NMZxltwRo8QtmkMRdAu8=" crossorigin="anonymous"></script>
  <script>
    $(function () {
      $('.btn-get-check').on('click', function () {
        var checkVal = '';
        $('[type="checkbox"][name="hoge[]"]').each(function (i, e) {
          if ($(e).is(':checked')) {
            checkVal = checkVal + $(e).val() + ',';
          }
        });
        $('.checked').text('チェック済みは：'+checkVal);
      });
      $('.btn-set-all-check').on('click', function() {
        $('[type="checkbox"][name="hoge[]"]').each(function (i, e) {
          $(e).prop('checked', true);
        });
      });
      $('.btn-set-all-un-check').on('click', function() {
        $('[type="checkbox"][name="hoge[]"]').each(function (i, e) {
          $(e).prop('checked', false);
        });
      });
      $('.btn-set-reverse-check').on('click', function() {
        $('[type="checkbox"][name="hoge[]"]').each(function (i, e) {
          $(e).prop('checked', !$(e).prop('checked'));
        });
      });
      $('.btn-set-2-check').on('click', function() {
        var control = $('[type="checkbox"][name="hoge[]"][value="2"]');
        control.prop('checked', !control.prop('checked'));
      });
    });
  </script>
</body>
</html>
```