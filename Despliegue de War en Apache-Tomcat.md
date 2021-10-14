# Despliegue de War en Apache Tomcat
 
 En la siguiente guía se explicará el despliegue de una aplicación web en el servidor web Tomcat gracias a su paquete .war

 # Creación de una App Web en Java

 ## Requisitos previos

 Haber seguido los pasos de la guía [Instalación de Apache Tomcat](https://github.com/gdborja/tomcat/blob/main/Instalaci%C3%B3n%20Apache%20Tomcat.md) y tener instalado maven.

 ## Construcción del proyecto

 Comenzar descargando el proyecto java del siguiente [enlace](https://github.com/jpexposito/docencia/tree/master/comun/ejemplos/java/app-web-demo) 

  Buscar el fichero ***web.xml*** y añadir en la etiqueta display-name su nombre:

```console
<display-name>app-web-nombreAPoner</display-name>
```

Sustituir en el fichero pom.xml la etiqueta finalName por el nombre introducido en la etiqueta anterior:

```console
<finalName>app-web-nombreAPoner</finalName>
```

Modificar el fichero index.jsp introduciendo de nuevo el nombre en el apartado alumno.

```console
<html>
    <body>
        <h1>Hola Mundo</h1>
        <p>Yo soy NombreAPoner</p>
    </body>
</html>
```

Ir a la ruta donde se encuentre el pom y ejecutar el comando:

```console
mvn clean install 
```

Una vez lanzado se creará un directorio ***target*** en el que se encuentra nuestro paquete **.war** el cual copiaremos en el directorio ***/opt/tomcat/apache-tomcat/weapps***

```console
sudo cp app-web-nombreAponer.war /opt/tomcat/apache-tomcat/webapps
```

Abrir el navegador y entrar en el panel administrador de tomcat. Se debería visualizar el paquete, clic en el mismo y se debería abrir una nueva pestaña en el navegador el resultado de la app.

- localhost:8082
- Manager App
- clic en app-web-nombreAPoner



  










