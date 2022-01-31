Acceso a Datos
--------------
>Para manejo de archivos de texto.

    Posibles modos:
    - Design patterns are not a silver bullet to all your problems.
    
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
  >
  
  
```
