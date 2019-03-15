# チェックボックス

- 概要
  - 単一の場合は$this->Form->checkbox、複数の場合は$this->Form->selectを使用する
    - ただし、複数の場合は「'multiple' => 'checkbox'」を設定する

- 単一のチェックボックス
  ```
  <!-- example 1 -->
  echo $this->Form->checkbox('done');

  <!-- example 1 html -->
  <input type="hidden" name="done" value="0">
  <input type="checkbox" name="done" value="1">


  <!-- example 2 -->
  echo $this->Form->checkbox('done', ['value' => 555, 'hiddenField' => false]);

  <!-- example 2 html -->
  <input type="checkbox" name="done" value="555"
  ```

- 複数のチェックボックス
  ```
  <!-- example 1 -->
  $options = [
    'Value 1' => 'Label 1',
    'Value 2' => 'Label 2'
  ];
  echo $this->Form->select('field', $options, ['multiple' => 'checkbox']);

  <!-- example 1 html -->
  <input name="field" value="" type="hidden">
  <div class="checkbox">
    <label for="field-1">
    <input name="field[]" value="Value 1" id="field-1" type="checkbox">
    Label 1
    </label>
  </div>
  <div class="checkbox">
    <label for="field-2">
    <input name="field[]" value="Value 2" id="field-2" type="checkbox">
    Label 2
    </label>
  </div>
  ```
- 注意点
  - 複数のチェックボックスの場合、配列となるので、登録する際は文字列にするなど、加工が必要である

- 参考
  - https://book.cakephp.org/3.0/ja/views/helpers/form.html