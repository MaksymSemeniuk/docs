###Форматирование вывода даты

string prepareDate($timestamp, $fieldType)

**$timestamp** - дата в формате Unix timestamp

**$fieldType** - вариант форматирования

+ DATE - формат вида Y-m-d. Приклад: "2007-04-30"
+ TIME - формат вида H:i:s. Приклад: "13:43:27"
+ YEAR - формат вида Y. Приклад: "2007"
+ DATETIME (по умолчанию) - формат вида Y-m-d H:i:s. Приклад: "2007-04-30 13:43:27"

***

####Приклад

	function getEvents( $date ) {  
		global $modx;  
		$output = '';  
		$fulldate = $modx->db->prepareDate( $date, 'DATE' );		
		//Преобразует дату в удобный для чтения вид   
		$result = $modx->db->select( 'event_name', 'events', 'timestamp = ' . intval( $date ) );  
		while( $row = $modx->db->getRow( $result ) ) {  
			$output .= $row['event_name'] . ' состоится ' . $fulldate . '.';  
		}  
	}