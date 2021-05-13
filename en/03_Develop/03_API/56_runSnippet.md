###Возвращает результат выполнения сніпета с заданными параметрами

string runSnippet(string $snippetName [, array $params]);

**$snippetName** - Назва сніпета (чувствительно к регистру!)

**$params** - массив со значениями параметров

***

####Приклад

	$txt = $modx->runSnippet('Ditto', 	array( 'startID' => 2, 
					'summarize' => 2, 
					'removeChunk' => 'Comments', 
					'tpl' => 'ditto_blog', 
					'paginate' => 1, 
					'extenders' => 'summary,dateFilter', 
					'paginateAlwaysShowLinks' => 1, 
					'tagData' => 'documentTags' 
					));

	//вернет результат работы сніпета Ditto, который идентичен вызову:
	[[Ditto? &startID=`2` &summarize=`2` &removeChunk=`Comments` &tpl=`ditto_blog` &paginate=`1` &extenders=`summary,dateFilter` &paginateAlwaysShowLinks=`1` &tagData=`documentTags`]]