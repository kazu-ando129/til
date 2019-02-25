# ログローテートの設定

## 初期設定
  - 世代：10
  - サイズ：10MB

## ソースコード
- FileLog.php
```FileLog.php
    protected $_defaultConfig = [
        'path' => null,
        'file' => null,
        'types' => null,
        'levels' => [],
        'scopes' => [],
        'rotate' => 10,
        'size' => 10485760, // 10MB
        'mask' => null,
    ];
```

## 設定変更
- config/app.php
  - rotate、sizeを設定する。設定しない場合は初期値が有効になる
```app.php
    'Log' => [
        'debug' => [
            'className' => 'Cake\Log\Engine\FileLog',
            'path' => LOGS,
            'file' => 'debug',
            'url' => env('LOG_DEBUG_URL', null),
            'scopes' => false,
            'levels' => ['notice', 'info', 'debug'],
            'rotate' => 30,
            'size' => '10MB'
        ],
        'error' => [
            'className' => 'Cake\Log\Engine\FileLog',
            'path' => LOGS,
            'file' => 'error',
            'url' => env('LOG_ERROR_URL', null),
            'scopes' => false,
            'levels' => ['warning', 'error', 'critical', 'alert', 'emergency'],
            'rotate' => 30,
            'size' => '10MB'
        ],
        // To enable this dedicated query log, you need set your datasource's log flag to true
        'queries' => [
            'className' => 'Cake\Log\Engine\FileLog',
            'path' => LOGS,
            'file' => 'queries',
            'url' => env('LOG_QUERIES_URL', null),
            'scopes' => ['queriesLog'],
        ],
    ],
```