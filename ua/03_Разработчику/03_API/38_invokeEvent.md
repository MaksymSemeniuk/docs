###Вызвать заданное событие

array invokeEvent(string $evtName, array $extParams);

**$evtName** - наименование события
**$extParams** - параметры события в виде набора значений name=>value

***

####Приклад

	$modx->invokeEvent("OnWebChangePassword", array( "userid" => $id, "username" => $username, "userpassword" => $newpwd ));