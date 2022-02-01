Acceso a Datos
--------------
Para manejo (lectura, modificacion) de archivos de texto.

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