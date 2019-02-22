# toggle

- 概要
  - HTMLに表示/非表示のアニメーションを設定する

- コード
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>toggle sample</title>
</head>
<body>
  <div>
    <button type="button" class="display-btn">表示する</button>
    <div class="display-area" style="display: none;">
      <p>hogehoge</p>
    </div>
  </div>
  <div>
    <button type="button" class="display-btn2">表示する2</button>
    <div class="display-area2" style="display: none;">
      <p>hogehoge2</p>
    </div>
  </div>
</body>
<script src="https://code.jquery.com/jquery-1.10.2.js"></script>
<script>
  $('.display-btn').on('click', function () {
    <!-- 表示/非表示を制御する -->
    $('.display-area').toggle(500, function () {
      console.log('finish');
    });
  });
  $('.display-btn2').on('click', function () {
    <!-- 高さを制御する -->
    $('.display-area2').slideToggle(500, function () {
      console.log('finish');
    });
  });
</script>
</html>
```

- 参考
  - https://api.jquery.com/toggle/
  - https://api.jquery.com/slideToggle/