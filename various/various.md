Varios
--------------
Otras funciones de uso diario, para consulta rapida
 * [Obtener la IP del servidor](#obtener-la-ip-del-servidor)
* [Obtener la URL actual](#obtener-url)
* [Modificar el Header para descargar un archivo](#descargar-archivo)

Posibles modos:
* w  - solo escritura.
* r  - solo lectura.
* a  - solo adicionar.
* w+ - lectura y escritura.
* a+ - solo adicionar,lectura y escritura.
* x  - nuevo archivosolo escritura.

```php
<?php
  $file = fopen("test.txt", 'w+');
  $size = filesize( $filename );
  $data = fread( $file, $size );
  fwrite($file, "Hola Mundo!!!");
  fclose($file);
?>
```
Tambien es posible leer y sobreescribir todo un archivo 

```php
<?php
	$archivo = file_get_contents('test.txt');
	$archivo = $archivo + " modificaciones ";
	file_put_contents('test.txt',$archivo);
?>
```

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
