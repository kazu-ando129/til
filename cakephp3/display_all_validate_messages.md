# バリデーションメッセージを一括表示する方法

- HogeConttoller.php

```HogeConttoller.php
public function add() {
    $hoge = $this->Hoge->newEntity();
    if ($this->request->is('post')) {
        $hoge = $this->Hoge->patchEntity($hoge, $this->request->getData());
        if ($this->Hoge->save($hoge)) {
            $this->redirect(['action' => 'index']);
        }
    }
    $this->set(compact('hoge'));
}
```


- Hoge/add.ctp

```add.ctp
<?php if (!empty($hoge->getErrors())): ?>
    <?php foreach($hoge->getErrors() as $key => $value): ?>
        <?php if (is_array($value)) : ?>
            <?php foreach($value as $key1 => $value1): ?>
            <?= $value1 ?><br>
            <?php endforeach; ?>
        <?php endif; ?>
    <?php endforeach; ?>
<?php endif; ?>
```