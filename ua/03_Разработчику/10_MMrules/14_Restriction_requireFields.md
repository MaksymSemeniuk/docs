###Виджет для плагина ManagerManager, позволяющий сделать поля документа или TV обязательными для заполнения. 

*Добавляет звёздочку красного цвета рядом с именем обязательного для заполнения поля, выдаёт сообщение при попытке сохранить не заполнив обязательные поля, предотвращая сохранение.*

mm_requireFields(string $fields, string $roles, string $templates);

####Опис параметров
Назва|Опис|Допустимые значения|Значення за замовчуванням|Обязателен?
--------|--------|---------|--------|--------
fields|Поля документа (или TV), которые должны быть обязательными.|{comma separated string}|—|true
roles|Роли, для которых необходимо применить виждет, пустое значение — все роли.|{comma separated string}|—|false
templates|Id шаблонов, для которых необходимо применить виджет, пустое значение — все шаблоны.|{comma separated string}|—|false

####Приклады
Сделать обязательным для заполнения заголовки и даты публикации всех документов
	
	mm_requireFields('pagetitle,pub_date');




