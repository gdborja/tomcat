# Instalación de Apache Tomcat en Linux

En la siguiente guía instalaremos el servicio web "Apache-Tomcat-10" en Ubuntu 20 para poder desplegar aplicaciones Java.

# Requisitos previos

Será necesario Ubuntu 20 o cualquier otra distro Linux, acceso a internet y permisos de administrador para el usuario. Además, tener instalado ***Java Open JDK**

# Instalación Apache Tomcat en local

Antes de comenzar actualizar repositorios del sistema y el sistema operativo

```console
sudo apt update && sudo apt upgrade
```
 Continuar descargando el paquete Tomcat 10 desde su [página oficial](https://tomcat.apache.org/download-10.cgi) con el comando wget:

 ```console
 wget https://downloads.apache.org/tomcat/tomcat-10/v10.0.12/bin/apache-tomcat-10.0.12.tar.gz 
 ``` 

 Descomprimir el paquete descargado en el directorio *** /opt/tomcat ***

 ```console
sudo tar xf apache-tomcat-10.0.12.tar.gz -C /opt/tomcat/ 
 ```

 Crear el usuario del sistema tomcat

 ```console
 sudo useradd -U -m -d /opt/tomcat -k /dev/null -s /bin/false tomcat 
 ```
 Asignar como propietario de los archivos del Tomcat 10 al usuario anteriormente creado

 ```console
sudo chown -R tomcat: /opt/tomcat/
 ```

 Renombrar el directorio de instalación creando un enlace un enlace simbólico.

 ```console
 sudo ln -s /opt/tomcat/apache-tomcat-10.0.12/ /opt/tomcat/apache-tomcat
 ```

Crear el fichero de configuración ***/etc/systemd/system/tomcat10.service***

```console
sudo nano /etc/systemd/system/tomcat10.service
```

Añadir e el fichero las siguientes líneas de configuración:

```console
[Unit]
Description=Tomcat 10.0 servlet container para Ubuntu 20.04 LTS
After=network.target
[Service]
Type=forking
User=tomcat
Group=tomcat
Environment="JAVA_OPTS=-Djava.security.egd=file:///dev/urandom"
Environment="CATALINA_BASE=/opt/tomcat/apache-tomcat"
Environment="CATALINA_HOME=/opt/tomcat/apache-tomcat"
Environment="CATALINA_PID=/opt/tomcat/apache-tomcat/temp/tomcat.pid"
Environment="CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC"
ExecStart=/opt/tomcat/apache-tomcat/bin/startup.sh
ExecStop=/opt/tomcat/apache-tomcat/bin/shutdown.sh
[Install]
WantedBy=multi-user.target
```

Iniciar el servicio y comprobar que se encuentra ejecutándose.

```console
sudo systemctl start tomcat10

systemctl status tomcat10
```

#Acceso a Apache Tomcat

Puede suceder que al instalar el servicio haya incompatibilidades de puertos, ya que pueden estar siendo utilizados por otros servicios. En caso de error cambiar la configuración del puerto en el fichero **server.xml** ubicado en ***/opt/tomcat/apache-tomcat-10.0.12/conf/***

```console
sudo nano /opt/tomcat/apache-tomcat-10.0.12/conf/server.xml
```

Cambiar la línea a :
```console
<Connector port="8082"
```

Reiniciar el servicio para que se guarde la configuración realizada.

```console
sudo systemctl restart tomcat10
```

Comprobar el funcionamiento del servicio web entrando desde el navegador.

```console
localhost:8082

ip:88082
```

