###Виджет для плагина ManagerManager, позволяющий создать новую произвольную вкладку на странице редактирования документа.

mm_createTab($name, $id, $roles, $templates, $intro, $width);

####Опис параметров
Назва|Опис|Допустимые значения|Значення за замовчуванням|Обязателен?
--------|--------|---------|--------|--------
name|Текст заголовка новой вкладки.|{string}|—|true
id|Уникальный id новой вкладки.|{string}|—|true
roles|Роли, для которых необходимо применить виждет, пустое значение — все роли.|{comma separated string}|—|false
templates|Id шаблонов, для которых необходимо применить виджет, пустое значение — все шаблоны.|{comma separated string}|—|false
intro|Опис новой вкладки, отображается в самом верху (можно использовать HTML).|{string}|—|false
width|Ширина содержимого новой вкладки, можно использовать css значения (наПриклад: '100%', '450px', 'auto').|{string}|680|false

####Приклады
Создать вкладку с заголовком «Категории» у всех документов для всех пользователей
 
	mm_createTab('Категории', 'mycats');
Создать новую вкладку шириной 450px с Описм у документов с id шаблона = 3 или 4
	
	mm_createTab('SEO', 'seoTab', '', '3,4', 'Здесь вы можете отредактировать всё, что касается поисковой оптимизации.', '450');