### Получение плейсхолдера

*Замечание: многие сніпеты имеют собственные плейсхолдеры, которые они обрабатывают самостоятельно. Метод getPlaceholder может о них ничего не знать.*

string getPlaceholder(string $name);

**$name** - Назва плейсхолдера. Задается без синтаксической конструкции.

***

####Приклад
```php
$txt = $modx->getPlaceholder('MyPlaceholder');
//вернет значение плейсхолдера MyPlaceholder.
```
***

####Исходный код
```php
/**
* Returns the placeholder value
*
* @param string $name Placeholder name
* @return string Placeholder value
*/
function getPlaceholder($name) {
    return isset($this->placeholders[$name]) ? $this->placeholders[$name] : null;
}
```