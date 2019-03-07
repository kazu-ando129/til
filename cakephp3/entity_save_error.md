# entity_save_error

- 概要
  - エンティティの保存で失敗したときのエラーを表示する

- 方法
  ```HogesController.php

  public function add()
  {
      if (!$this->Hoge->save($hoge)) {
          $this->log(print_r($hoge->errors(),true), LOG_DEBUG);
      }
  }