Varios
--------------
Otras funciones de uso diario, para consulta rapida
 * [Obtener la IP del servidor](#obtener-la-ip-del-servidor)
 * [Obtener la URL actual](#obtener-la-url-actual)
 * [Modificar el Header para descargar un archivo](#modificar-el-header-para-descargar-un-archivo)

Obtener la IP del servidor
--------------------------
```php
<?php
	if (!empty($_SERVER['HTTP_CLIENT_IP'])) {
    	$ip = $_SERVER['HTTP_CLIENT_IP'];
		} elseif (!empty($_SERVER['HTTP_X_FORWARDED_FOR'])) {
    		$ip = $_SERVER['HTTP_X_FORWARDED_FOR'];
		} else {
    		$ip = $_SERVER['REMOTE_ADDR'];
		}
?>
```

Obtener la URL actual
=====================
```php
<?php
	$ruta= $_SERVER['REQUEST_SCHEME'] . '://' . $_SERVER['HTTP_HOST'] . str_replace( "menu_ppal","", $_SERVER["REQUEST_URI"]);
?>
```

Modificar el Header para descargar un archivo
=============================================
```php
<?php
	$pathToFile = "http://localhost/files/test.txt"
    header('Content-Type: application/octet-stream');
    header('Content-Disposition: attachment; filename='.basename($pathToFile));
    header('Expires: 0');
    header('Cache-Control: must-revalidate');
    header('Pragma: public');
    header('Content-Length: ' . filesize($pathToFile));
	

?>
```
