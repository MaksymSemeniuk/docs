
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>ListChild: Примеры</h2>

<h3 class="sub-header text-bold">Динамический список дочерних документов</h3>
<p>Пример использования в backend (административной панели)</p>
<p>Сниппет сформирует список в виде: <code>параметр1==значение1||параметр2==значение2</code></p>
<p>Создайте TV-параметр с типом ввода DropDown List Menu.</p>
<p>В возможных значениях укажите:</p>
<pre class="brush: php;">@EVAL return $modx-&gt;runSnippet('ListChild', array('docid' =&gt; 10, 'where' =&gt; 'isfolder = 1 and hidemenu = 0'));</pre>
<p>Отобразит все опубликованные и неудаленные дочерние контейнеры папки 10, которые отмечены для показа в меню.</p>
<p>Или так:</p>
<pre class="brush: php;">@EVAL return $modx-&gt;runSnippet('ListChild', array('docid' =&gt; '10,11,12', 'depth' =&gt; 2));</pre>
<p>Отобразит все опубликованные и неудаленные дочерние документы, в том числе и контейнеры, папок 10, 11 и 12 до второго уровня вложенности.</p>

<h3 class="sub-header text-bold">Выпадающий список (frontend)</h3>
<p><span class="text-bold">Пример использования во frontend (пользовательской части)</span></p>
<p>Сниппет сформирует список в виде: <code>&lt;option value="значение"&gt;параметр&lt;/option&gt;</code></p>
<p>Разместите в шаблоне следующий код:</p>
<pre class="brush: html;">
&lt;form action="[~[*id*]~]"&gt;
	&lt;select class="form-control"&gt;
		[[ListChild? &docid=`152` &depth=`1` &where=`isfolder = 0` &emptyfield=`0`]]
	&lt;/select&gt;
&lt;/form&gt;
</pre>
<div class="well">
	<form action="listchild/primery.html">
		<select class="form-control">
			
		</select>
	</form>
</div>
<p>Отобразит в виде раскрывающегося списка все опубликованные и неудаленные дочерние документы папки 4, до второго уровня вложенности, которые не являются контейнерами.</p>
<p class="alert alert-info">Обратите внимание, что в данном примере после выбора из списка любого пункта, форма перегружается и выбранное значение сбрасывается.</p>
<p><span class="text-bold">Пример использования во frontend с запоминанием выбранных значений</span></p>
<p>Тегу <code>select</code> добавьте атрибут <code>name</code>. Значение атрибута укажите в соответствующем параметре сниппета.</p>
<p class="alert alert-danger">Важно! Не используйте для разных списков одинаковые значения атрибута <span class="text-bold">name</span>.</p>
<pre class="brush: html;">
&lt;form action="[~[*id*]~]"&gt;
	&lt;select onchange="this.form.submit();" name="dropdown"  class="form-control"&gt;
		[[ListChild? &docid=`18` &name=`dropdown` &emptyfield=`0`]]
	&lt;/select&gt;
&lt;/form&gt;
</pre>
<div class="well">
	<form action="listchild/primery.html">
		<select onchange="this.form.submit();" name="dropdown" class="form-control">
			<option value="159" >AjaxSearch</option><option value="160" >AnythingRating</option><option value="327" >BlackList</option><option value="161" >Breadcrumbs</option><option value="344" >CfgTv</option><option value="162" >CodeMirror</option><option value="156" >countViews</option><option value="419" >ddGetMultipleField</option><option value="149" >ddMMEditor</option><option value="321" >ddTypograph</option><option value="163" >Ditto</option><option value="428" >DLBuildMenu</option><option value="17" >DLCrumbs</option><option value="383" >DLLastViews</option><option value="370" >DLMenu</option><option value="329" >DLRequest</option><option value="247" >DLSiblings</option><option value="164" >DocInfo</option><option value="353" >DocLister</option><option value="165" >Easy Newsletter</option><option value="166" >eForm</option><option value="167" >FirstChildRedirect</option><option value="168" >Forgot Manager Login</option><option value="303" >FormLister</option><option value="169" >GetField</option><option value="170" >if</option><option value="345" >imageCaptor</option><option value="171" >Jot</option><option value="343" >LikeDislike</option><option value="172" >ListChild</option><option value="173" >ListIndexer</option><option value="174" >ManagerManager</option><option value="175" >MaxiGallery</option><option value="176" >MemberCheck</option><option value="177" >MetaX</option><option value="407" >ModxAccount</option><option value="178" >MODxBB и phpBB</option><option value="179" >multiTV</option><option value="324" >OpenGraphTags</option><option value="318" >optimizeJPG</option><option value="180" >Personalize</option><option value="181" >phpthumb</option><option value="182" >PHx</option><option value="157" >Preview Next</option><option value="183" >Reflect</option><option value="158" >Sass</option><option value="371" >Selector</option><option value="184" >Shopkeeper</option><option value="331" >SimpleFiles</option><option value="342" >SimpleGallery</option><option value="330" >SimpleTube</option><option value="185" >SiteMap</option><option value="418" >Star Rating</option><option value="186" >tagLinks</option><option value="351" >TagSaver</option><option value="194" >thumb</option><option value="187" >TransAlias</option><option value="188" >TvTagCloud</option><option value="189" >UltimateParent</option><option value="190" >Wayfinder</option><option value="193" >WebLogin</option><option value="191" >WebLoginPE</option><option value="192" >WebSignup</option><option value="297" >Yams</option>
		</select>
	</form>
</div>
<p>Теперь после выбора из списка любого пункта, форма перегружается но выбранное значение сохраняется.</p>
<p>Событие <code>onchange="this.form.submit();"</code> автоматически отправляет данные формы после каждого изменения элемента формы.</p>

<h3 class="sub-header text-bold">Переключатели radio (frontend)</h3>
<p><span class="text-bold">Пример c использованием шаблона в frontend</span></p>
<p><span class="text-bold">1.</span> Задача - вывести в виде переключателей.</p>
<pre class="brush: html;">
[[ListChild? &docid=`152` &name=`radio` &tpl=`tplRadio` &selectedValue=`checked="checked"` &emptyfield=`0`]]
</pre>
<p><span class="text-bold">Шаблон tplRadio:</span></p>
<pre class="brush: html;">
&lt;div class="col-lg-3 col-sm-4 col-xs-6"&gt;
	&lt;div class="radio"&gt;
		&lt;label&gt;
			&lt;input type="radio" name="radio" class="colored-blue" value="" onchange="this.form.submit();"&gt;
			&lt;span class="text"&gt; &lt;/span&gt;
		&lt;/label&gt;
	&lt;/div&gt;
&lt;/div&gt;
</pre>
<p>Отобразит в виде переключателей все опубликованные и неудаленные дочерние документы папки 4, без пустого поля в начале списка. Запомнит выбранное значение.</p>
<div class="row">
	<div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="159" onchange="this.form.submit();">
			<span class="text"> AjaxSearch</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="160" onchange="this.form.submit();">
			<span class="text"> AnythingRating</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="327" onchange="this.form.submit();">
			<span class="text"> BlackList</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="161" onchange="this.form.submit();">
			<span class="text"> Breadcrumbs</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="344" onchange="this.form.submit();">
			<span class="text"> CfgTv</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="162" onchange="this.form.submit();">
			<span class="text"> CodeMirror</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="156" onchange="this.form.submit();">
			<span class="text"> countViews</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="419" onchange="this.form.submit();">
			<span class="text"> ddGetMultipleField</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="149" onchange="this.form.submit();">
			<span class="text"> ddMMEditor</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="321" onchange="this.form.submit();">
			<span class="text"> ddTypograph</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="163" onchange="this.form.submit();">
			<span class="text"> Ditto</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="428" onchange="this.form.submit();">
			<span class="text"> DLBuildMenu</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="17" onchange="this.form.submit();">
			<span class="text"> DLCrumbs</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="383" onchange="this.form.submit();">
			<span class="text"> DLLastViews</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="370" onchange="this.form.submit();">
			<span class="text"> DLMenu</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="329" onchange="this.form.submit();">
			<span class="text"> DLRequest</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="247" onchange="this.form.submit();">
			<span class="text"> DLSiblings</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="164" onchange="this.form.submit();">
			<span class="text"> DocInfo</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="353" onchange="this.form.submit();">
			<span class="text"> DocLister</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="165" onchange="this.form.submit();">
			<span class="text"> Easy Newsletter</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="166" onchange="this.form.submit();">
			<span class="text"> eForm</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="167" onchange="this.form.submit();">
			<span class="text"> FirstChildRedirect</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="168" onchange="this.form.submit();">
			<span class="text"> Forgot Manager Login</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="303" onchange="this.form.submit();">
			<span class="text"> FormLister</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="169" onchange="this.form.submit();">
			<span class="text"> GetField</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="170" onchange="this.form.submit();">
			<span class="text"> if</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="345" onchange="this.form.submit();">
			<span class="text"> imageCaptor</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="171" onchange="this.form.submit();">
			<span class="text"> Jot</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="343" onchange="this.form.submit();">
			<span class="text"> LikeDislike</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="172" onchange="this.form.submit();">
			<span class="text"> ListChild</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="173" onchange="this.form.submit();">
			<span class="text"> ListIndexer</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="174" onchange="this.form.submit();">
			<span class="text"> ManagerManager</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="175" onchange="this.form.submit();">
			<span class="text"> MaxiGallery</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="176" onchange="this.form.submit();">
			<span class="text"> MemberCheck</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="177" onchange="this.form.submit();">
			<span class="text"> MetaX</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="407" onchange="this.form.submit();">
			<span class="text"> ModxAccount</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="178" onchange="this.form.submit();">
			<span class="text"> MODxBB и phpBB</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="179" onchange="this.form.submit();">
			<span class="text"> multiTV</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="324" onchange="this.form.submit();">
			<span class="text"> OpenGraphTags</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="318" onchange="this.form.submit();">
			<span class="text"> optimizeJPG</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="180" onchange="this.form.submit();">
			<span class="text"> Personalize</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="181" onchange="this.form.submit();">
			<span class="text"> phpthumb</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="182" onchange="this.form.submit();">
			<span class="text"> PHx</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="157" onchange="this.form.submit();">
			<span class="text"> Preview Next</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="183" onchange="this.form.submit();">
			<span class="text"> Reflect</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="158" onchange="this.form.submit();">
			<span class="text"> Sass</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="371" onchange="this.form.submit();">
			<span class="text"> Selector</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="184" onchange="this.form.submit();">
			<span class="text"> Shopkeeper</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="331" onchange="this.form.submit();">
			<span class="text"> SimpleFiles</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="342" onchange="this.form.submit();">
			<span class="text"> SimpleGallery</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="330" onchange="this.form.submit();">
			<span class="text"> SimpleTube</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="185" onchange="this.form.submit();">
			<span class="text"> SiteMap</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="418" onchange="this.form.submit();">
			<span class="text"> Star Rating</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="186" onchange="this.form.submit();">
			<span class="text"> tagLinks</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="351" onchange="this.form.submit();">
			<span class="text"> TagSaver</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="194" onchange="this.form.submit();">
			<span class="text"> thumb</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="187" onchange="this.form.submit();">
			<span class="text"> TransAlias</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="188" onchange="this.form.submit();">
			<span class="text"> TvTagCloud</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="189" onchange="this.form.submit();">
			<span class="text"> UltimateParent</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="190" onchange="this.form.submit();">
			<span class="text"> Wayfinder</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="193" onchange="this.form.submit();">
			<span class="text"> WebLogin</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="191" onchange="this.form.submit();">
			<span class="text"> WebLoginPE</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="192" onchange="this.form.submit();">
			<span class="text"> WebSignup</span>
		</label>
	</div>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<div class="radio">
		<label>
			<input type="radio" name="radio" class="colored-blue" value="297" onchange="this.form.submit();">
			<span class="text"> Yams</span>
		</label>
	</div>
</div>
</div>

<h3 class="sub-header text-bold">Флажки checkbox (frontend)</h3>
<p><span class="text-bold">Пример c использованием шаблона в frontend</span></p>
<p>Задача - вывести в виде переключателей.</p>
<pre class="brush: html;">[[ListChild? &docid=`152` &name=`checkbox` &tpl=`tplCheckbox` &selectedValue=`checked="checked"` &emptyfield=`0`]]</pre>
<p><span class="text-bold">Шаблон tplCheckbox:</span></p>
<pre class="brush: html;">
&lt;div class="col-lg-2 col-sm-4 col-xs-6"&gt;
	&lt;label class="csscheckbox csscheckbox-primary"&gt;
		&lt;input type="checkbox" name="checkbox" class="colored-blue" value="" onchange="this.form.submit();"&gt;
		&lt;span&gt;&lt;/span&gt; 
	&lt;/label&gt;
&lt;/div&gt;
</pre>
<div class="row">
	<div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="159" onchange="this.form.submit();">
		<span></span> AjaxSearch
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="160" onchange="this.form.submit();">
		<span></span> AnythingRating
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="327" onchange="this.form.submit();">
		<span></span> BlackList
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="161" onchange="this.form.submit();">
		<span></span> Breadcrumbs
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="344" onchange="this.form.submit();">
		<span></span> CfgTv
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="162" onchange="this.form.submit();">
		<span></span> CodeMirror
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="156" onchange="this.form.submit();">
		<span></span> countViews
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="419" onchange="this.form.submit();">
		<span></span> ddGetMultipleField
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="149" onchange="this.form.submit();">
		<span></span> ddMMEditor
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="321" onchange="this.form.submit();">
		<span></span> ddTypograph
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="163" onchange="this.form.submit();">
		<span></span> Ditto
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="428" onchange="this.form.submit();">
		<span></span> DLBuildMenu
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="17" onchange="this.form.submit();">
		<span></span> DLCrumbs
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="383" onchange="this.form.submit();">
		<span></span> DLLastViews
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="370" onchange="this.form.submit();">
		<span></span> DLMenu
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="329" onchange="this.form.submit();">
		<span></span> DLRequest
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="247" onchange="this.form.submit();">
		<span></span> DLSiblings
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="164" onchange="this.form.submit();">
		<span></span> DocInfo
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="353" onchange="this.form.submit();">
		<span></span> DocLister
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="165" onchange="this.form.submit();">
		<span></span> Easy Newsletter
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="166" onchange="this.form.submit();">
		<span></span> eForm
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="167" onchange="this.form.submit();">
		<span></span> FirstChildRedirect
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="168" onchange="this.form.submit();">
		<span></span> Forgot Manager Login
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="303" onchange="this.form.submit();">
		<span></span> FormLister
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="169" onchange="this.form.submit();">
		<span></span> GetField
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="170" onchange="this.form.submit();">
		<span></span> if
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="345" onchange="this.form.submit();">
		<span></span> imageCaptor
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="171" onchange="this.form.submit();">
		<span></span> Jot
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="343" onchange="this.form.submit();">
		<span></span> LikeDislike
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="172" onchange="this.form.submit();">
		<span></span> ListChild
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="173" onchange="this.form.submit();">
		<span></span> ListIndexer
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="174" onchange="this.form.submit();">
		<span></span> ManagerManager
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="175" onchange="this.form.submit();">
		<span></span> MaxiGallery
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="176" onchange="this.form.submit();">
		<span></span> MemberCheck
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="177" onchange="this.form.submit();">
		<span></span> MetaX
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="407" onchange="this.form.submit();">
		<span></span> ModxAccount
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="178" onchange="this.form.submit();">
		<span></span> MODxBB и phpBB
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="179" onchange="this.form.submit();">
		<span></span> multiTV
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="324" onchange="this.form.submit();">
		<span></span> OpenGraphTags
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="318" onchange="this.form.submit();">
		<span></span> optimizeJPG
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="180" onchange="this.form.submit();">
		<span></span> Personalize
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="181" onchange="this.form.submit();">
		<span></span> phpthumb
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="182" onchange="this.form.submit();">
		<span></span> PHx
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="157" onchange="this.form.submit();">
		<span></span> Preview Next
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="183" onchange="this.form.submit();">
		<span></span> Reflect
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="158" onchange="this.form.submit();">
		<span></span> Sass
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="371" onchange="this.form.submit();">
		<span></span> Selector
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="184" onchange="this.form.submit();">
		<span></span> Shopkeeper
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="331" onchange="this.form.submit();">
		<span></span> SimpleFiles
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="342" onchange="this.form.submit();">
		<span></span> SimpleGallery
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="330" onchange="this.form.submit();">
		<span></span> SimpleTube
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="185" onchange="this.form.submit();">
		<span></span> SiteMap
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="418" onchange="this.form.submit();">
		<span></span> Star Rating
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="186" onchange="this.form.submit();">
		<span></span> tagLinks
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="351" onchange="this.form.submit();">
		<span></span> TagSaver
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="194" onchange="this.form.submit();">
		<span></span> thumb
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="187" onchange="this.form.submit();">
		<span></span> TransAlias
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="188" onchange="this.form.submit();">
		<span></span> TvTagCloud
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="189" onchange="this.form.submit();">
		<span></span> UltimateParent
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="190" onchange="this.form.submit();">
		<span></span> Wayfinder
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="193" onchange="this.form.submit();">
		<span></span> WebLogin
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="191" onchange="this.form.submit();">
		<span></span> WebLoginPE
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="192" onchange="this.form.submit();">
		<span></span> WebSignup
	</label>
</div><div class="col-lg-2 col-sm-4 col-xs-6">
	<label class="csscheckbox csscheckbox-primary">
		<input type="checkbox" name="checkbox" class="colored-blue" value="297" onchange="this.form.submit();">
		<span></span> Yams
	</label>
</div>
</div>
<p>Отобразит в виде переключателей все опубликованные и неудаленные дочерние документы папки 4, без пустого поля в начале списка.</p>

<h3 class="sub-header text-bold">Количество найденных документов</h3>
<p><span class="text-bold">Вывод количества найденных документов</span></p>
<pre class="brush: html;">[[ListChild? &docid=`152` &count=`1`]]</pre>
<p>Отобразит количество опубликованных и неудаленных дочерних документов папки 4.</p>

<h3 class="sub-header text-bold">Вывод id найденных документов</h3>
<p><span class="text-bold">Вывод идентификаторов найденных документов</span></p>
<pre class="brush: html;">[[ListChild? &docid=`152` &tpl=`idTpl` &emptyfield=`0` &separator=`,`]]</pre>
<p>Чанк <span class="text-bold">idTpl</span>:</p>
<pre class="brush: html;">[+value+]</pre>
<p>Отобразит список id всех опубликованных и неудаленных дочерних документов папки 4, разделенных запятой. </p>
<p><span class="text-bold">Вывод заголовков найденных документов</span></p>
<p>По аналогии с id документа, можно вывести любую переменную шаблона (кроме TV-параметров). Например, если нужно вывести заголовки:</p>
<pre class="brush: html;">[[ListChild? &docid=`152` &tpl=`idTpl` &emptyfield=`0` &separator=`, ` &value=`pagetitle`]]</pre>
<p>Отобразит заголовки всех опубликованных и неудаленных дочерних документов папки 4, разделенных запятой с пробелом.</p>

<h3 class="sub-header text-bold">Использование параметра where</h3>
<p>При использовании параметра <span class="text-bold">where</span> необходимо заменять все <code>=</code> на <code>@eq</code>. Например, для того, чтобы вывести идентификаторы всех документов с шаблоном 5 и menuindex равным 0, размещаем такой вызов:</p>
<pre class="brush: html;">[[ListChild? &docid=`0` &depth=`10` &tpl=`tplId` &emptyfield=`0` &separator=`, ` &where=`template @eq 5 and menuindex @eq 0`]]</pre>
<p>Чанк <span class="text-bold">tplId</span>:</p>
<pre class="brush: html;">[+value+]</pre>

<h3 class="sub-header text-bold">Анонс статей или подменю</h3>
<p><span class="text-bold">Выводим анонс статей</span></p>
<pre class="brush: html;">&lt;ul&gt;[[ListChild? &docid=`152` &emptyfield=`0` &tpl=`tplNews` &limit=`3` &sort=`menuindex` &dir=`DESC`]]&lt;/ul&gt;</pre>
<p>Чанк tplNews:</p>
<pre class="brush: html;">&lt;li&gt;&lt;a href="[~[+value+]~]"&gt;[+param+]&lt;/a&gt;&lt;p&gt;[+desc+]&lt;/p&gt;&lt;/li&gt;</pre>
<p>Отобразит анонсы трех статей с кратким описанием.</p>
<p><span class="text-bold">Выводим подменю</span></p>
<pre class="brush: html;">&lt;ul&gt;[[ListChild? &docid=`152` &emptyfield=`0` &tpl=`tplSubmenu` &limit=`3` &sort=`menuindex` &dir=`DESC`]]&lt;/ul&gt;</pre>
<p>Чанк tplSubmenu:</p>
<pre class="brush: html;">&lt;li&gt;&lt;a href="[~[+value+]~]"&gt;[+param+]&lt;/a&gt;&lt;/li&gt;</pre>