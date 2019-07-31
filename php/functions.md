# functions

- range : ある範囲の整数の配列を作成
  - range ( mixed $start , mixed $end [, number $step = 1 ] ) : array
  - 使用例
  ```range.php
  range(1, 10)
  // array(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)

  range(1, 10, 2)
  // array(1, 3, 5, 7, 9)
  ```
- array_slice : 配列の一部を展開する
  - array_slice ( array $array , int $offset [, int $length = NULL [, bool $preserve_keys = FALSE ]] ) : array
  - 使用例
  ```sample.php
  $input = ["a", "b", "c", "d", "e"];
  $output = array_slice($input, 0, 3);   // ["a", "b", "c"]
  $output = array_slice($input, 2);      // ["c", "d", "e"]
