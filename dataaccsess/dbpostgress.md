Acceso a Datos
--------------
Una simple clase para ejecutar consultas a una base de datos postgres, requiere incluir el driver php_pdo_pgsql.dll en php.ini

```php
    class DbPostgres{
          public  $dbName='';
          public  $hostIp='';
          public  $hostPort='';
          public  $dbUser='';
          public  $dbPassword='';
          private $dbConnection='';
          
        public function runQuery($sql)
        {
            $dataSet='';
            
            if ( empty($this->dbConn)  ) {
              if ( $this->dbName != '' && $hostIp != '' && $hostIp != ''  && $hostPort!= ''  &&  $dbUser!= '' && $dbPassword!= '' ) {
                  $this->dbConnection = pg_connect("host=" . $this->hostIp . " port=" . $this->$hostPort . " dbname=" . $this->dbName . " user=" . $this->dbUser . " password=" . $this->dbPassword);
              }
            }
            
           if(!empty($this->dbConnection)){
                $dataSet = pg_query($this->dbConnection, $sql);
            }
            return $dataSet;    
        }
    }
