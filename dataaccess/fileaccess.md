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
	$file = file_get_contents('test.txt');
	$file = $file + " nuevo texto a adicionar ";
	file_put_contents('test.txt',$file);
?>
```

Creacion de unarchivo enformat csv
```php
<?php
	$fileCsv = fopen("test.csv", 'w+');

	// rs es un resulset obtenido de una consulta sql
	foreach($rs as $row)
	{
		fputcsv($file, $row, ";");
	}

	fclose($fileCsv);
?>
```

Empaquetado de archivos en ZIP y modificacion del header para su descarga
```php
<?php
	$filezip= "mifile.zip";
	$zip = new ZipArchive;
	if ($zip->open($filezip, ZipArchive::CREATE) === TRUE) 
	{
		$zip->addFile("", "test1.txt");
		$zip->addFile("", "test2.txt");
		$zip->addFile("", "test3.txt");
		$zip->close();
	}

	header("Pragma: public");
	header("Expires: 0");
	header("Cache-Control: must-revalidate, post-check=0, pre-check=0");
	header("Cache-Control: public");
	header("Content-Description: File Transfer");
	header("Content-type: application/octet-stream");
	header('Content-Disposition: attachment; filename="mifile.zip"');
	header("Content-Transfer-Encoding: binary");
	header("Content-Length: ".filesize($filezip));
	@readfile($filezip);
?>
```