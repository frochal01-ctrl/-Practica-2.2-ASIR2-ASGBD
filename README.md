# -Practica-2.2-ASIR2-ASGBD
## Desplegar Oracle Database 23ai Free con Podman 
Configuracion de la maquina virtual
<img src="images/vt.png">  
<img src="images/vb.png">  
1. Preparar Podman y descargar la imagen  
   
sudo apt update  
<img src="images/Captura de pantalla de 2026-10-07 13-38-06.png" >  
sudo apt install podman  
<img src="images/podman.png">  
sudo podman pull container-registry.oracle.com/database/free:23.5.0.0  
<img src="images/oracle.png">  
sudo podman images  
<img src="images/pi.png">  

2.Crear y comprobar el contenedor  
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


