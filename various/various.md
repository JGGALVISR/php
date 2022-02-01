Varios
--------------
Otras funciones de uso diario, para consulta rapida

* [Obtener la IP del servidor](#obtener-ip)

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
==========================
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