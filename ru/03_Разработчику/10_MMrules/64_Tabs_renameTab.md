###Виджет для плагина ManagerManager, позволяющий переименовать одну из стандартных вкладок на странице редактирования документа.

mm_renameTab($tabId, $newlabel, $roles, $templates);

####Опис параметров
Назва|Опис|Допустимые значения|Значення за замовчуванням|Обязателен?
--------|--------|---------|--------|--------
tabId|вкладки, которую необходимо переименовать.|{'general'; 'settings'; 'access'}|—|true
newlabel|Новый текст заголовка вкладки.|{string}|—|true
roles|Роли, для которых необходимо применить виждет, пустое значение — все роли.|{comma separated string}|—|false
templates|Id шаблонов, для которых необходимо применить виджет, пустое значение — все шаблоны.|{comma separated string}|—|false

####Приклады
Переименовать вкладку «Общие» для пользователей с id роли = 2
	
	mm_renameTab('general', 'Основное', '2');
Переименовать вкладку «Настройки страницы» для всех пользователей
	
	mm_renameTab('settings', 'Настроечки');