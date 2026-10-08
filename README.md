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




