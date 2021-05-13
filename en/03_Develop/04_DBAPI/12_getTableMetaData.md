###Информация о структуре таблицы

array getTableMetaData($table)

**$table** - Назва таблицы

Эта функция возвращает многомерный массив с подробной информацией о структуре заданной таблицы MySQL.

Массив имеет вид *TableField => Array( Info => Value )*, где 

+ TableField - Назва колонки, 
+ Info - одно из 6 информационных параметров, 
+ Value - значение конкретного параметра.

***

####Информационные параметры:

**Field** - Назва поля таблицы
**Type** - тип поля и размер (наПриклад int(5), varchar(40) или text)
**Null** - может содержать значение NULL
**Key** - содержит ключ для значения типа "UNI" (UNIQUE) или "PRI" (PRIMARY)
**Default** - Значення за замовчуванням
**Extra** - дополнительная информация, такая как использование auto_increment

***

####Приклад

	$table = 'my_table';  
	$data = $modx->db->getTableMetaData( $table );  
	$output = '';   
	
	// Цикл по всем колонкам  
	foreach( $data as $field => $arr ) {	 
	
		// Назва колонки 
		$output .= '<b>' . $field . '</b><br />';
		
		// Цикл по всем информационным параметрам
		foreach( $arr as $info => $value )
			$output .= $info . ': ' . $value . '<br />'; // Вывод значения  
		}  
	}
	return $output;