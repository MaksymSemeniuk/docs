###Возвращает массив пользовательских групп, в которых текущий пользователь участвует

*Замечание: Функция учитывает тип пользователя и возвращает для менеджера группы при нахождении в системе управления, а для пользователя на сайте.*

mixed getUserDocGroups([bool $resolveIds]);

**$resolveIds** - возвращать названия групп вместо идентификаторов.

***

####Приклад

	$txt = $modx->getUserDocGroups(true); 
	print_r($txt); 
	
	/* полученный результат: 
	Array ( [0] => Site Admin Pages ) 
	*/