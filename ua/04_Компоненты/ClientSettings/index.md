Автор: <a href="https://github.com/mnoskov/clientsettings">mnoskov</a>

<img src="https://img.shields.io/badge/PHP-%3E=5.6-green.svg?php=5.6">

Модуль для створення форми налаштувань.

Для початку роботи потрібно перейменувати файли конфігурації `assets/modules/clientsettings/config/*.php.sample` в `*.php`.

Конфігурація полів береться з файлів `*.php` з папки `/assets/modules/clientsettings/config/`. Кожен файл - це окрема вкладка. Такий спосіб зберігання дозволяє легко змінювати і переносити конфігурацію.

Приклад файлу конфігурації:
```php
<?php

return [
    'caption' => 'Заголовок табу',
    'introtext' => 'Опис табу',
    'settings' => [
        'field_text' => [
            'caption' => 'Текст',
            'type'  => 'text',
            'note'  => 'Це просто текст',
            'default_text' => 'Значення за замовчуванням',
        ],
        
        ...
        
    ],
];
```

Типи полів описані <a href="/info/terminology-2/chto_takoe_parametr.html">тут</a>.

Крім стандартних полів можна використовувати тип `divider` для поділу списку полів на групи:
```php
'field_text' => [
    'caption' => 'Тема групи полів',
    'type'  => 'divider',
],
```
