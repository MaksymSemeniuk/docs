# Встроенные модификаторы

Являются встроенной заменой плагину PHx.
Включаются параметром `enable_filter` в общих настройках сайта.

## Преимущества

+ Легковесные по сравненинию с PHx
+ Можно использовать в чанкках и сніпетах
+ Гибкость
+ Легко читать
+ Не зависят от разделителей: ( ' " `
+ Много вариантов модификаторов
+ Совместимы с плагином PHx
+ Могут использоваться одновременно с плагином PHx
	
## Приклады:

Приклад 1: варианты оформления

```
[*longtitle:ifempty=[*pagetitle*]*]
[*longtitle:ifempty='[*pagetitle*]'*]
[*longtitle:ifempty="[*pagetitle*]"*]
[*longtitle:ifempty([*pagetitle*])*]
[*longtitle:ifempty('[*pagetitle*]')*]
```

Приклад 2: регистронезависимость

```
[*template:is(1):then(Top page):else(Sub page)*]
[*template:IS(1):THEN('Top page'):ELSE('Sub page')*]
```

Приклад 3: оформление в несколько строк

```
[*id
:is(1)
:then(Top)
:else(Other)
*]
```

Ещё Приклады:

```
[*email:spam_protect*]
[*price:number_format*]
[*content:addBreak*]
[*pagetitle:strip_tags*]
[(site_name:escape)]
{{Chunk:escape}}
[+placeholder:escape+]
[[Snippet:escape?param=1&param2]]
[!$_SERVER['REQUEST_TIME']:dateFormat('Y-m-d H:i:s')!]
[*pict:is_image:tpl('<img src="[+value+]" alt="">')*]
[+image:isNotEmpty
  :then('<img src="[[phpthumb? &input=`[+image+]` &options=`w=300`]]" alt="">')
  :else('[+wf.linktext:substr(0,1)+]')
  +]
[*pub_date:ifEmpty('[*publishedon*]'):dateformat=`%d.%m.%Y`*]
```
