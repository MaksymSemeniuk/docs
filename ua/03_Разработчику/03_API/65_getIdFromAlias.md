Возвращает идентификатор документа по его урл
```
string getIdFromAlias(string $alias);
```
**$alias** - псевдоним документа

### Приклад
```
	$id = $modx->getIdFromAlias('folder/folder/doc.html')
	//id документа doc.html
```
