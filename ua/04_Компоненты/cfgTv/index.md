
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>CfgTv: системні настройки зі списку ТВ параметрів із зазначеного документа Створює системні настройки зі списку ТВ параметрів із зазначеного документа</h3>
Створює системні настройки зі списку ТВ параметрів із зазначеного документа.
<p>Багато хто любить і активно юзают настройки сайту через <code>[[getField? name=`tv_name` ...]]]</code>, створюючи ресурс де всі ці настройки в TV лежать. Але от невдача, кожна така настройка = 1 запиту, а значить і час генерації більше + незручно.</p>
<p>А що якщо робити також, але виклик на сторінці буде <code>[(cfg_footer_phone)]</code>, <code>[(cfg_icq)]</code> і так далі зручно правда?</p>
<p>Рішення: CfgTv</p>
<p>Подія: <code>OnBeforeDocFormSave</code></p>
<pre class="brush: php;">
/**
 * CfgTv 0.1
 * Save TV as system setting from some resourse 
 * 
 *
 * @category    plugin
 * @version     1.0.0b
 * @author      Bumkaka
 * @internal    @properties &ids=ID ресурсів налаштувань;text;347 &prefix=Префікс;text;cfg_
 * @internal    @events OnBeforeDocFormSave
 * @internal    @modx_category Manager and Admin
 */

$e = &$modx->event;
switch($e->name){
    case 'OnBeforeDocFormSave':
		$list_id = explode(',',$ids);
		if(!in_array($_POST['id'],$list_id)) return;
		
		$SQL = "SELECT * FROM ".$modx->getFullTableName('site_tmplvars').";";
		$result = $modx->db->query($SQL);
		
		while($row = $modx->db->getRow($result)){
			$TVNAME[$row['id']] = $row['name'];
		}
		
		foreach($_POST as $key => $value){
			if (substr($key,0,2)!='tv') continue;
			$id=substr($key,2,strlen($key));
			$name=$prefix.$TVNAME[$id];
			$settings[$name]=$value;
			$SQL="SELECT * FROM ".$modx->getFullTableName('system_settings')." WHERE `setting_name`='".$name."'";
			$count=$modx->db->getRow($modx->db->query($SQL));
			if (!empty($count['setting_name'])){
				$SQL="UPDATE ".$modx->getFullTableName('system_settings')." SET `setting_value`='".$value."' WHERE `setting_name`='".$name."'";
				$modx->db->query($SQL);
			} else {
				$SQL="INSERT into ".$modx->getFullTableName('system_settings')." SET `setting_name`='".$name."',`setting_value`='".$value."'";
				$modx->db->query($SQL);
			}
		}
    break;
}
</pre>