# プルダウンの選択

```sample.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>selectbox sample</title>
</head>
<body>
  <div>
    <p>single selected box</p>
    <select name="single">
      <option value="">選択してください</option>
      <option value="html">html</option>
      <option value="css">css</option>
      <option value="javascript">javascript</option>
    </select>
    <button type="button" class="btn-html">htmlを選択</button>
  </div>
  <div>
    <p>multiple selected box</p>
    <select name="multiple" multiple="multiple">
      <option value="html">html</option>
      <option value="css">css</option>
      <option value="javascript">javascript</option>
    </select>
    <button type="button" class="btn-html-css">htmlとcssを選択</button>
  </div>
  <script src="http://code.jquery.com/jquery-3.3.1.min.js"
    integrity="sha256-FgpCb/KJQlLNfOu91ta32o/NMZxltwRo8QtmkMRdAu8=" crossorigin="anonymous"></script>
  <script>
    $(function () {
      $('[name="single"], [name="multiple"]').on('change', function() {
        alert($(this).val());
      });
      $('.btn-html').on('click', function() {
        // valだけだと、changeイベントは発火しないので、triggerでchangeイベントを発火する
        $('[name="single"]').val('html');
        $('[name="single"]').trigger('change');
      });
      $('.btn-html-css').on('click', function() {
        // valだけだと、changeイベントは発火しないので、triggerでchangeイベントを発火する
        $('[name="multiple"]').val(['html', 'css']);
        $('[name="multiple"]').trigger('change');
      });
    });
  </script>
</body>
</html>
```