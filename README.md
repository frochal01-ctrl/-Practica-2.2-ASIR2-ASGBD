# -Practica-2.2-ASIR2-ASGBD
1. Desplegar Oracle Database 23ai Free con Podman 
Configuracion de la maquina virtual
<img src="images/vt.png">  
<img src="images/vb.png">  
   1.1 Preparar Podman y descargar la imagen  
   
sudo apt update  
<img src="images/Captura de pantalla de 2026-10-07 13-38-06.png" >  
sudo apt install podman  
<img src="images/podman.png">  
sudo podman pull container-registry.oracle.com/database/free:23.5.0.0  
<img src="images/oracle.png">  
sudo podman images  
<img src="images/pi.png">  

   1.2 Crear y comprobar el contenedor  
sudo podman volume create oracle_23ai_datos  
<img src="images/ov.png">  
sudo podman run -d --name cont-oracle -p 1521:1521 --restart=always -v oracle_23ai_datos:/opt/oracle/oradata:U container-
registry.oracle.com/database/free:23.5.0.0  
<img src="images/c.png">  
sudo podman ps
<img src="images/ps">  
sudo podman ps -a  
<img src="images/ps -a.png">  
sudo podman logs cont-oracle
<img src="images/logs.png">  
3.Entrar en Oracle y crear el usuario de trabajo  
sudo podman exec -it cont-oracle /bin/bash  
<img src="images/ex.png">  
sudo podman exec -it cont-oracle sqlplus / as sysdba  
<img src="images/sql.png"> 
```sql
ALTER SESSION SET CONTAINER = FREEPDB1;
CREATE USER orauser IDENTIFIED BY "TU_CLAVE";
GRANT CREATE SESSION, CREATE TABLE TO orauser;
ALTER USER orauser QUOTA 100M ON USERS;
EXIT;
```  
<img src="images/spl2.png">  
sudo podman exec -it cont-oracle sqlplus orauser@//localhost:1521/FREEPDB1  
<img src="images/funciona.png"> 
2. Desplegar PostgreSQL
sudo apt install postgresql postgresql-contrib php-pgsql  
<img src="images/installpost.png">  
sudo systemctl start postgresql
<img src="images/starpost.png">   
sudo systemctl enable postgresql  
<img src="images/enablepost.png">  
sudo -i -u postgres
<img src="images/-upost.png">  
psql  
<img src="images/psql.png">  

```sql
CREATE DATABASE dbpg;
CREATE USER pguser WITH PASSWORD 'TU_CLAVE';
GRANT ALL PRIVILEGES ON DATABASE dbpg TO pguser;
\q
```
<img src="images/q.png">  
psql -h localhost -U pguser -d dbpg -W  
<img src="images/funciona1.png">  
3. Desplegar MariaDB
sudo apt install mariadb-server mariadb-client
<img src="images/installmaria.png">  
sudo systemctl enable --now mariadb  
<img src="images/enablemaria.png">
sudo mariadb
<img src="images/sudomaria.png">

