###Задает значение плейсхолдера с учетом префикса

*Замечание: если в качестве значения был передан объект или массив, то работа передается методу toPlaceholders.*

void toPlaceholders(string $key, string $value[, string $prefix]);

**$key** - Назва плейсхолдера
**$value** - значение плейсхолдера.
**$prefix** - префик, который будет добавлен перед Назвам плейсхолдера
По умолчанию: пусто

***

####Приклад

	// Установим плейсхолдер 
	MyPlaceholder $modx->toPlaceholder('MyPlaceholder', 'Я люблю MODX','test.'); 
	
	// Выведем некий текст для проверки плейсхолдеров 
	echo '[+test.MyPlaceholder+] за его гибкость и мощность!'; 
	
	// полученный результат: 
	// Я люблю MODx за его гибкость и мощность!