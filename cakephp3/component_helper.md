# ComponentとHelperの使い方

- 概要
  - Componentとは、Controllerで共有するロジックの集まりのことを指す
  - Helperとは、プレゼンテーション層（View、Element、Layout）のためのComponentのようなクラスのこと

- 作り方
  - Component（Example1Component.phpを作成する）
  ```bash
  $ sh bin/cake bake Component Example1
  ```

  - Helper（Example2Helper.phpを作成する）
  ```bash
  $ sh bin/cake bake Helper Example2
  ```

- 使い方
  - Component
    - コントローラーでロードする

    ```AppController.php
    $this->loadComponent('Example1');
    ```

- Component（Example1Component）からComponent（Example3Component）の呼び出し
```Example1Component.php
namespace App\Controller\Component;

use Cake\Controller\Component;
use Cake\Controller\ComponentRegistry;

class Example1Component extends Component {

    public $components = [ 'Example3' ];

    public function hoge2()
    {
        return $this->Example3->hoge();
    }
}
```

```Example3Component.php
namespace App\Controller\Component;

use Cake\Controller\Component;
use Cake\Controller\ComponentRegistry;

class Example3Component extends Component {

    protected $_defaultConfig = [];

    public function hoge()
    {
        return 'hoge';
    }
}
```


- Component（Example1Component）からHelper（Example2Helper）の呼び出し
```Example1Component.php
namespace App\Controller\Component;

use Cake\Controller\Component;
use Cake\Controller\ComponentRegistry;

use Cake\View\View;
use App\View\Helper\Example2Helper

class Example1Component extends Component {

    public function initialize(array $config)
    {
        parent::initialize($config);
        $this->Example2 = new Example2Helper(new View(), []);
    }

    public function hoge2()
    {
        return $this->Example2->hogeHelper();
    }
}
```

```Example2Helper.php
namespace App\View\Helper;

use Cake\View\Helper;
use Cake\View\View;

class Example2Helper extends Helper {

    protected $_defaultConfig = [];

    public function hogeHelper()
    {
        return 'helper';
    }
}
```


- Helper（Example2Helper）からComponent（Example1Component）の呼び出し
```Example2Helper.php
namespace App\View\Helper;

use Cake\View\Helper;
use Cake\View\View;

use App\Controller\Component\Example1Component;
use Cake\Controller\ComponentRegistry;

class Example2Helper extends Helper {

    protected $_defaultConfig = [];

    public function initialize(array $config)
    {
        parent::initialize($config);
        $this->Example1 = new Example1Component(new ComponentRegistry(), []);
    }

    public function hogeHelper()
    {
        return $this->Example1->hoge2();
    }
}
```

```Example1Component.php
namespace App\Controller\Component;

use Cake\Controller\Component;
use Cake\Controller\ComponentRegistry;

class Example1Component extends Component {

    public function hoge2()
    {
        return 'hoge2';
    }
}
```