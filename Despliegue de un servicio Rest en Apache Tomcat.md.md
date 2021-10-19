# Despligue de un servicio REST en Apache Tomcat

En el siguiente repositorio se va a mostrar como desplegar una API REST en Apache Tomcat gracias a Jersey

# Requisitos previos

Disponer de Java JDK, Maven, permisos de administrador y haber realizado los pasos del [repositorio anterior](https://github.com/gdborja/tomcat/blob/main/Despliegue%20de%20War%20en%20Apache-Tomcat.md)

# Construcción del servicio

Descargar el proyecto del promotor de este ejercicio [jpexposito](https://jpexposito.com/) en el siguiente [enlace](https://github.com/jpexposito/docencia/tree/master/comun/ejemplos/java/rest-service)

Una vez descargado generar el fichero ***.war*** , copiar el mismo en el directorio pertinente como se muestra en el anterior repositorio 

```console
mvn clean install 
sudo cp fichero.war /opt/tomcat/apache-tomcat/webapps

```

 Entrar en el gestor de aplicaciones del servidor web y desplegar la app.

 ##  Problemas durante el despligue 

 Intencionadamente va a ocurrir un error durante el despliegue. Este está causado a posta para indagar en los ficheros .log del servidor y así familiarizarnos con la búsqueda de este y tener una idea de cómo resolverlo.
 En modo administrador 
 ```console
 cd /opt/tomcat/apache-tomcat/logs
 
 ```

 Buscar en los ficheros ***localhost.fechaHoy.log*** donde se muestran los problemas de acceso, dependencias de librerías etc, o en el fichero ***catalina.fechaHoy.log*** 

 Para solventar ese tipo de problemas debemos de incluir las librerías en el war o dentro de la carpeta lib de Tomcat,  o dentro de la carpeta WEB-INFO/lib del proyecto.

